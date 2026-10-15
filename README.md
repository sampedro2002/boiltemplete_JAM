# boiltemplete_JAM

Boilerplate JAM (frontend estático que consume APIs) con React + Vite + TypeScript + Tailwind.

## Stack

- React 19, Vite, TypeScript
- Tailwind CSS 4 (`@tailwindcss/vite`)
- React Router (`react-router-dom`)
- Zustand (estado global)
- React Hook Form + Zod + `@hookform/resolvers` (formularios y validación)
- Axios (cliente HTTP)
- ESLint + Prettier (`eslint-config-prettier`)

## Instalar requisitos

### Node.js + npm (npm viene incluido con Node)

**Windows 10 / 11**

```powershell
# Opción A: winget (Win 11 y Win 10 reciente; si no existe, usa la opción B)
winget install OpenJS.NodeJS.LTS

# Opción B: instalador .msi LTS desde https://nodejs.org (marca "Add to PATH")
```

**Linux (recomendado: nvm, no requiere sudo)**

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
# cierra y abre la terminal, luego:
nvm install --lts
```

En Debian/Ubuntu evita `apt install nodejs npm` (trae versiones viejas).

Verifica en cualquier sistema (abre una terminal nueva):

```bash
node -v   # v22 o superior
npm -v
```

## Plataformas soportadas

Windows 10, Windows 11 y Linux (también macOS). Requisito: Node.js 22+ y npm.

| Acción      | Linux / macOS / Git Bash | Windows PowerShell            | Windows cmd                  |
| ----------- | ------------------------ | ----------------------------- | ---------------------------- |
| Copiar .env | `cp .env.example .env`   | `Copy-Item .env.example .env` | `copy .env.example .env`     |

Los finales de línea están forzados a LF (`.gitattributes`, `.editorconfig`, Prettier `endOfLine: lf`) para que nada cambie al moverte de plataforma. El resto de comandos (`npm ...`) es idéntico en todos.

## Conectar tu API

1. Copia `.env.example` a `.env` y pon la URL: `VITE_API_URL=https://tu-api.com/api`
2. Usa el cliente de `src/api/client.ts`: `api.get('/recurso')`.
3. Si tu API no permite CORS desde `http://localhost:5173`, habilítalo en el servidor.
4. Reinicia `npm run dev` tras cambiar el `.env`.

## Uso

```bash
npm install
cp .env.example .env   # ajusta VITE_API_URL
npm run dev
```

## Scripts

| Script                | Descripción                 |
| --------------------- | --------------------------- |
| `npm run dev`         | Servidor de desarrollo      |
| `npm run build`       | Build de producción (`dist`) |
| `npm run preview`     | Previsualiza el build       |
| `npm run lint`        | ESLint                      |
| `npm run format`      | Prettier (escribe)          |
| `npm run format:check`| Prettier (solo verifica)    |

## Estructura

```
src/
  api/         cliente axios y llamadas a la API
  components/  componentes reutilizables
  hooks/       custom hooks
  pages/       páginas (una por ruta)
  routes/      configuración de rutas
  schemas/     esquemas zod
  store/       stores de zustand
```

## Instalación manual de librerías (referencia)

```bash
npm install axios react-router-dom zustand react-hook-form zod @hookform/resolvers tailwindcss @tailwindcss/vite
npm install -D prettier eslint-config-prettier
```
