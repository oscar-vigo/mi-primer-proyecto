# Ajustes de GitHub para mi-primer-proyecto

Este archivo describe ajustes administrativos; su presencia no los activa.

## Rama principal

En [Settings → Rules → Rulesets](https://github.com/oscar-vigo/mi-primer-proyecto/settings/rules), si el plan lo permite, crea una regla activa para `main`:

- Exigir pull request antes de integrar cambios. Si mantienes el repositorio solo, no exijas una aprobación que no puedas dar a tu propia PR.
- Bloquear pushes forzados y borrado de la rama.
- Cuando Actions vuelva a estar disponible y sus comprobaciones pasen, exigir los checks de CI existentes antes de fusionar. No selecciones checks inexistentes o desactivados.

GitHub Free puede limitar estas protecciones en repositorios privados. No se han sustituido por checks que aparenten proteger la rama.

## Secretos y permisos

En **Settings → Security → Advanced Security / Code security**, activa Dependency graph, Dependabot alerts, Dependabot security updates y Grouped security updates donde existan dependencias. Activa Secret scanning y Push protection si están disponibles en tu plan; la protección de secretos de repositorios privados puede requerir una licencia adicional.

Guarda credenciales en **Settings → Secrets and variables → Actions** o en el proveedor de despliegue, sin incluirlas en código, PR, logs ni archivos de ejemplo. Si una credencial se publica, revócala y rótala.

En **Settings → Actions → General → Workflow permissions**, selecciona **Read repository contents and packages permissions** como valor por defecto. Los jobs que publican versiones o cambios declaran sus permisos de escritura explícitamente. No habilites la aprobación automática de PR por Actions si no la necesitas.

## Ramas y repositorios

En [Settings → General](https://github.com/oscar-vigo/mi-primer-proyecto/settings), activa **Automatically delete head branches**. Esto elimina ramas después de fusionar PR; no elimina `main`.

Archiva un repositorio únicamente cuando hayas confirmado que no depende de él ningún despliegue, dominio o proceso. Esta configuración no archiva ni borra repositorios.

## Preview y producción

Si este repositorio despliega una web, revisa en Vercel o Netlify que la rama de producción sea `main` y que las PR usen previews. Separa credenciales y bases de datos de preview y producción; no expongas secretos de producción a PR de forks. Estos ajustes se aplican en el proveedor y no se modifican desde este archivo.
