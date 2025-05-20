# Proyecto Ionic con Navegación Híbrida, Login y AuthGuard usando Standalone Components

Este proyecto es un ejemplo básico de una aplicación Ionic + Angular con:

- Navegación híbrida usando Angular Router y NavController.
- Login simple con formulario y token falso en `localStorage`.
- Protección de rutas con `AuthGuard`.
- Uso de standalone components (sin módulos tradicionales).
- Lazy loading de páginas con `loadComponent`.
- Logout para cerrar sesión.
- Estructura modular y escalable.

---

## Contenido

- [Estructura del proyecto](#estructura-del-proyecto)
- [Navegación y rutas](#navegación-y-rutas)
- [Login y AuthGuard](#login-y-authguard)
- [Standalone Components](#standalone-components)
- [Uso de NavController](#uso-de-navcontroller)
- [Logout](#logout)
- [Comandos usados](#comandos-usados)
- [Próximos pasos](#próximos-pasos)

---

## Estructura del proyecto

- `/src/app/pages/auth/auth.page.ts` - Página de login con formulario y validación.
- `/src/app/pages/auth/auth.page.html` - Template HTML del formulario.
- `/src/app/pages/tabs/tabs.page.ts` - Página principal protegida, con botón de logout.
- `/src/app/guards/auth.guard.ts` - Guard para proteger rutas que requieren login.
- `/src/app/app.routes.ts` - Configuración de rutas con lazy loading y guard.

---

## Navegación y rutas

Se configuraron las rutas en `app.routes.ts` usando standalone components y lazy loading:

```ts
const routes: Routes = [
  { path: '', redirectTo: 'auth', pathMatch: 'full' },
  { path: 'auth', loadComponent: () => import('./pages/auth/auth.page').then(m => m.AuthPage) },
  { path: 'tabs', canActivate: [AuthGuard], loadComponent: () => import('./pages/tabs/tabs.page').then(m => m.TabsPage) },
];
