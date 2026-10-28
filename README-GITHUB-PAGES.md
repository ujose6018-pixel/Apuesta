# NBA Live en GitHub Pages

Esta app es una web estática: no necesita Node.js ni un servidor backend. Firebase se conecta desde el navegador con el SDK modular.

## Publicar
1. Abre **Settings → Pages** en el repositorio.
2. En **Build and deployment**, selecciona **GitHub Actions** como fuente.
3. Integra la rama `nba-live-github-pages` a `main` mediante el pull request de esta mejora.
4. Tras el merge, GitHub Actions publicará `index.html` automáticamente. La URL aparece en Settings → Pages y en el resumen del workflow.

## Firebase
- Proyecto configurado: `nba-marcador`.
- Firestore debe estar habilitado.
- Publica manualmente las reglas desde `firestore.rules` en Firebase Console o con Firebase CLI.
- Las reglas temporales solicitadas permiten lectura/escritura pública hasta el 24 de noviembre de 2026. Cualquier visitante podría editar o borrar datos mientras estén así. Antes de usarla públicamente, configura Authentication y reglas más restrictivas.
- Las claves de configuración web de Firebase son identificadores públicos; la seguridad real se hace con las reglas de Firestore.

## Datos y funciones
- Colección Firestore: `nbaMatches`.
- Marcador global, partidos y apuestas se sincronizan en tiempo real.
- Selector de los 30 equipos NBA con logos, controles +1/+2/+3 y lluvia de +3 a pantalla completa en cada triple (también se ve en los demás dispositivos conectados).
- Tipos de apuesta: Más/Menos, Hándicap, Ganador con Pago Anticipado (+20, guarda la ventaja máxima) y Puntos de jugador con botones +1/+2/+3.
- Líneas enteras muestran push ("faltan X para push · X+1 para ganar").
- Monto y cuota opcionales por apuesta: muestra cobro posible y total en juego.
- Los márgenes UNDER/OVER y hándicap se recalculan en vivo.
