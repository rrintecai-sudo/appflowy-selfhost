# appflowy-selfhost

Despliegue self-hosted de **AppFlowy Cloud** para `notes.rrintecai.co`, sobre
**Hostinger VPS + Easypanel**. Base para la app de workspace/notas con marca propia
(alternativa a Notion).

## Contenido
- `docker-compose.yml` — stack adaptado para Easypanel (nginx sin puertos al host ni TLS propio; el TLS lo pone Easypanel).
- `nginx/nginx.conf` — reverse proxy interno HTTP-only con el enrutamiento de AppFlowy (`/`, `/api`, `/ws`, `/gotrue`, `/minio`, `/console`).

## Variables de entorno
No se versionan (ver `.gitignore`). Se configuran en el campo **Environment** del
servicio Compose en Easypanel. Ver la plantilla oficial en el repo upstream
(`deploy.env`) para la lista completa.

## Cómo se despliega
Easypanel (proyecto `appflowy`, servicio `stack`) clona este repo y ejecuta el
compose. El dominio `notes.rrintecai.co` apunta al servicio `nginx` (puerto 80),
con SSL gestionado por Easypanel.

## Rutas
- `/` — la app (AppFlowy Web)
- `/console` — panel de administración (crear usuarios manualmente)

## Origen
Basado en [AppFlowy-IO/AppFlowy-Cloud](https://github.com/AppFlowy-IO/AppFlowy-Cloud) (AGPL-3.0).
