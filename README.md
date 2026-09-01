# Bolo11 — Datos de ligas

Este repo alimenta la web de Bolo11 con los datos de ligas y torneos.
Cada liga/torneo es **un fichero JSON en `ligas/`**, nombrado con su slug
(p. ej. `ligas/liga-vaguada-2025.json`).

## Qué cambiar según la situación

### Cada jornada (lo más frecuente)
En el fichero de la liga, actualiza:
- `currentRound`: número de la última jornada jugada (`totalRounds` no cambia).
- `zonaCampeonato` y `zonaConsolacion`: arrays de equipos con `pos, equipo, bolos, partidas, promedio, puntos`.
- `individualStandings`: array de jugadoras/es con `posGeneral, posFemenina, genero, califica, hdcp, maxPartida, bolos, partidas, promedio, jugador, equipo`.
- `jornadaResults`: añade la jornada recién jugada al array (o actualiza la última): `numero, vuelta, maxPuntosPorPartido, campeonato[], consolacion[], puntosJornada, libraron`.
- `nextJornada`: `announcement, date, libran[]`.
- `records`: si hay nueva máxima partida.

### Al iniciar una liga/torneo
- `status`: `upcoming` → `active` al empezar; `finished` al terminar.
- `eventDates`, `totalRounds` y composición inicial de las zonas.

### Fijos (no tocar durante la temporada)
- `slug`, `name`, `venue`, `season`, `type`, `gallery`.

## Cómo publicar
1. Edita el fichero (web de GitHub o git).
2. Comenta el cambio (p. ej. «Jornada 8 — Liga Vaguada»).
3. La web recoge los cambios en ~1 hora (caché horaria). No hace falta desplegar nada.

## Reglas
- Un fichero por liga: no mezcles ligas en el mismo fichero.
- Los campos `name, venue, season, type, status` son obligatorios siempre.
- Si una zona no tiene datos, déjala como `[]` (o omítela).
- Si rompes el JSON sin querer, la web muestra la última copia estable: repón el fichero y en ~1 hora vuelve la normalidad.
