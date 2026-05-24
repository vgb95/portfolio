# Guía de Despliegue en GitHub Pages

## Requisitos Previos

1. Una cuenta en GitHub
2. Node.js v20+ instalado
3. Git configurado localmente

## Pasos de Despliegue

### 1. Crear repositorio en GitHub

```bash
# Ir a https://github.com/new
# Crear un repositorio con nombre: portfolio
# NO inicializar con README (ya existe)
```

### 2. Configurar remote y push

```bash
cd /Users/valentin/Code/portfolio

# Reemplaza con tu usuario de GitHub
git remote add origin https://github.com/TU_USUARIO/portfolio.git
git branch -M main
git push -u origin main
```

### 3. Habilitar GitHub Pages

1. Ve a tu repositorio en GitHub
2. Ve a **Settings** > **Pages**
3. En "Source", selecciona **Deploy from a branch**
4. Selecciona rama: **main** y folder: **/root**
5. Click en **Save**

### 4. Configurar GitHub Actions

El workflow ya está configurado en `.github/workflows/deploy.yml`

Cada vez que hagas push a `main`, GitHub Actions automáticamente:

- Instala dependencias
- Hace build del proyecto
- Despliega a GitHub Pages

### 5. Verificar despliegue

- Después de hacer push, ve a **Actions** en tu repositorio
- Espera a que el workflow termine
- Tu portfolio estará disponible en: `https://vgb95.github.io/portfolio`

## Actualizar contenido

Para actualizar tu portfolio:

```bash
# Editar archivos en src/
vim src/components/Hero.astro
vim src/components/Contact.astro
# etc...

# Hacer commit y push
git add -A
git commit -m "Update portfolio content"
git push origin main
```

## Estructura de archivos importante

```
src/
├── pages/index.astro          → Página principal
├── components/
│   ├── Hero.astro             → Sección de presentación
│   ├── About.astro            → Sección Sobre mí
│   ├── Experience.astro       → Sección de experiencia
│   ├── Projects.astro         → Sección de proyectos
│   ├── Contact.astro          → Sección de contacto
│   ├── Navbar.astro           → Barra de navegación
│   └── ShanksIllustration.astro → Ilustración SVG
└── styles/
    └── global.css             → Estilos globales
```

## Dominio personalizado (Opcional)

Si tienes un dominio propio:

1. En GitHub: **Settings** > **Pages** > **Custom domain**
2. Ingresa tu dominio (ej: valentin.com)
3. Configura los DNS records de tu dominio:
   - CNAME → `TU_USUARIO.github.io`

## Problemas comunes

### El workflow falla

- Verifica que el `postcss.config.cjs` sea CommonJS
- Asegúrate de que Node.js sea v20+

### Estilos no se aplican

- Ejecuta `npm run build` localmente para verificar
- Asegúrate de que Tailwind está correctamente configurado

### Página se ve vacía

- Verifica que el repositorio es **público**
- Comprueba que GitHub Pages está habilitado

## Desarrollo local

```bash
# Instalar dependencias (una sola vez)
npm install

# Ejecutar servidor local
npm run dev
# Visita http://localhost:4321/portfolio

# Build para producción
npm run build

# Preview de build
npm run preview
```

---

¡Tu portfolio está listo para ser visto por el mundo! 🚀
