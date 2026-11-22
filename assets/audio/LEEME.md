# Audio de los videos de InvertirFácil

Generado el 21-nov-2026. Todo es composición original y síntesis propia: notas, ritmos, mezcla y efectos se escribieron en los scripts de `herramientas/` de la marca, que no están en este repositorio. No hay voz, texto a voz, música de terceros ni samples de origen desconocido. Lo único que no se sintetiza aquí son los instrumentos de la soundfont MuseScore_General (licencia MIT, abajo), con los que se tocan las partituras de las camas. La firma sonora aprobada (`../firma-sonora-invertirfacil.wav`, SHA-256 `95bfa5b0…2154`) no cambia y no se toca.

## Archivos

| Archivo | Qué es | Duración | SHA-256 |
|---|---|---|---|
| `cama-A-inicio.wav` | cama A, primeros 6 s sin colas (arranque limpio) | 6.0 s | `1e92761fa69836d60f6d855fe70532d7f6e6debba3a57134985e775586964718` |
| `cama-A.wav` | cama A, loop de 24 compases | 64.0 s | `4669b4a41e40c892342c237009b62b6e86af455b279a2203ff3da4058700306b` |
| `cama-A-final.wav` | cama A, acorde final | 5.5 s | `51069bced394734eaa25c141b98f56d69f9ee7ee9b419cdf60c724bddaa1b020` |
| `cama-B-inicio.wav` | cama B, primeros 6 s | 6.0 s | `e314cc2722f21da96c62180aed0f3a078e8067f11eb2e6a6050cbb4fa50aa26a` |
| `cama-B.wav` | cama B, loop de 32 compases | 68.57 s | `4bf15740cf6fc67d648c7a10cc3e56dc87a451b36f7b49b65f2ae0195339cc8a` |
| `cama-B-final.wav` | cama B, acorde final con cuerdas sostenidas | 5.5 s | `5e577d659551f2ff2898f719fab84342c16164976b005caef7f4b8cf63160be5` |
| `cama-C-inicio.wav` | cama C, primeros 6 s | 6.0 s | `2e6230e0dbdad93515884a7286184323732141a049fca998f2881a59555ad416` |
| `cama-C.wav` | cama C, loop de 28 compases | 68.57 s | `e70ffc1f339419cfafe012a1b72aac8a9082f5587e9ad833ef26f7b3c7dd8d50` |
| `cama-C-final.wav` | cama C, acorde final | 5.5 s | `91724e09b637473bb2b1c4c905f4eaf308466ec0a4631dcb3533683de6f9487f` |
| `sfx-whoosh.wav` | cambio de escena (punto fuerte a 0.32 s) | 0.50 s | `6f03cd7391e9f7e60bb275d3631d6c30b635011cbbef54162b82ed57024048b8` |
| `sfx-pop.wav` | aparece una cifra | 0.16 s | `12f6597f24c541bc8d7dde05848bb59af0a1c4113b38ff0e9e0faa4f13415895` |
| `sfx-tick.wav` | tecleo, cuenta regresiva, contadores, cursor | 0.05 s | `bced31954032a80acbd6705ac361adb83aaf75fcd233c637a7dcbfaf59e5ca6b` |
| `sfx-trazo.wav` | tachado (uno por renglón) | 0.34 s | `804f2a44679bf55e194f4b32a8dae91cd8182a1f70e5be90e2e59d7c58eddc11` |
| `sfx-subida.wav` | barras que crecen y contadores (termina en su ancla) | 0.90 s | `3f6d6d780923430b973bebda0a5b8646465f2552697f72e6c307c2c4e6f87096` |
| `sfx-golpe.wav` | golpe suave del cierre | 1.20 s | `71188c19d26b34829efda07ab1e3b5b98dd73656cc18ebcff699f895084ebb97` |

Todos: WAV PCM de 16 bits, estéreo, 44.1 kHz, con dither TPDF determinista. Los mismos SHA-256 están en `CAMAS` y `SFX` de `genvid.py`; si un archivo falta o cambia, el generador se detiene. `camas-procedencia.json` y `sfx-procedencia.json` guardan lo mismo que esta tabla y las mediciones de cada render.

## Cómo se generan (deterministas)

```bash
python3 herramientas/componer_camas.py "soundfont/MS Basic.sf3" assets/audio/   # camas (unos 90 s)
python3 herramientas/sintetizar_sfx.py assets/audio/                            # efectos (segundos)
python3 herramientas/medir_audio.py cama assets/audio/cama-A.wav --bpm 90       # mediciones
```

Se corrió cada script dos veces y salieron los mismos SHA-256. Entorno: Python 3.13, FluidSynth 2.3.4 (libfluidsynth3 de Ubuntu 24.04, llamado con ctypes desde `herramientas/fluid.py`, sin paquetes de PyPI), numpy 2.5.3 y scipy 1.18.1. Con otras versiones el resultado puede cambiar en el último bit; si se regeneran, hay que poner los SHA-256 nuevos en `genvid.py`.

## Soundfont

- Archivo: `MS Basic.sf3`, 51,278,610 bytes, SHA-256 `5ea2375e8bd7d8e71def1036978c1621e85b66934169b6a2744b27b9b3c2d99c`.
- Origen: repo oficial de MuseScore, https://github.com/musescore/MuseScore, ruta `share/sound/MS Basic.sf3`, commit `08d70c1a6ae0f5553603507c32e6db5379ad75d9` (20-nov-2026), objeto git `5be56b2fafa5eee347256cbe0d2fbfacd01702b6`. Con ese commit: https://raw.githubusercontent.com/musescore/MuseScore/08d70c1a6ae0f5553603507c32e6db5379ad75d9/share/sound/MS%20Basic.sf3
- Cómo se obtuvo: clon parcial del repo (sin blobs), lista del árbol con `git ls-tree` para encontrar la ruta y `git cat-file` del blob. `git hash-object` del archivo bajado da el mismo id del árbol, así que es byte por byte el del repo.
- Qué es por dentro (bloque INFO del archivo): `INAM` "MuseScore_General_HQ v0.2"; `ICOP` "Frank Wen 2000-02, Michael Cowgill 2014-17, S. Christian Collins 2018-20"; `ICMT` "Released under the MIT license. Please see "MuseScore_General_HQ-License.md" for more information."
- Licencia: `share/sound/MS Basic_License.md` del mismo commit (objeto `5071e8f2c2850acbd1d867d359267e37a3794ba3`; copia completa junto a estos archivos: `licencia-soundfont.md`). Dice: "MuseScore_General.sf2 is shared under the MIT license as described in COPYING, as was FluidR3Mono and FluidR3 before it." Y el COPYING: "Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software." Además: "The acknowledgements and copyright notices above must be included in any derivative work."
- Avisos que la licencia pide conservar: FluidR3 (original version) by Frank Wen Copyright (c) 2000-02; Mono conversion (FluidR3Mono) by Michael Cowgill Copyright (c) 2014-17; Adaptation for MuseScore_General.sf2 by S. Christian Collins Copyright (c) 2018-19; Temple Blocks instrument provided by Ethan Winer Copyright (c) 2002; Drumline Cymbals provided by Michael Schorsch Copyright (c) 2016. (Las camas no usan temple blocks ni platillos de marcha.)
- Detalle a saber: el texto de la licencia nombra "MuseScore_General.sf2, versión 0.2 del 13-may-2020" y el archivo se llama a sí mismo "MuseScore_General_HQ v0.2". Mismo autor, misma versión y mismos términos MIT; el repo instala los dos juntos (`share/sound/CMakeLists.txt`).
- Por qué no `FluidR3Mono_GM.sf3` del mismo repo: por dentro es "MS_General v0.1" y su licencia dice "The licensing for this new collection is currently under discussion and may be subject to change before release."
- No se usó `/usr/share/sounds/sf2/TimGM6mb.sf2` (GPL-2).
- Los avisos de arriba van aquí, junto a los archivos, y al final del texto de cada publicación con música (Instagram, TikTok y la descripción de YouTube): es la línea CREDITO_MUSICA de genvid.py, que el generador exige en modo música.

## Las tres camas

Progresiones diatónicas y ritmo cuantizado a semicorcheas (FluidSynth aplica cada nota al inicio de un bloque de 64 muestras: a lo más 1.45 ms de redondeo). Cada cama arranca con energía en el primer tiempo (bombo, bajo y acorde en la muestra 0, sin desvanecido) y su loop empata con su principio.

| | A, lo-fi | B, explicativa enérgica | C, curiosidad o tensión ligera |
|---|---|---|---|
| Tempo | 90 BPM | 112 BPM | 98 BPM |
| Tonalidad | Fa mayor | Do mayor | La menor |
| Loop | 24 compases, 64.0 s | 32 compases, 68.57 s | 28 compases, 68.57 s |
| Progresión | IVmaj9 iii7 ii9 V9sus-V9 (1-8 y 17-24), Imaj9 vi7 ii9 V9sus-V9 (9-16) | I V vi IV (1-8 y 17-24), IV V iii vi IV V vi V (9-16 y 25-32) | i VI iv v con pedal de La (1-8 y 17-24), VI VII i i VI VII v v (9-16), VI VII v v (25-28) |
| Instrumentos (banco:preset) | Tine Electric Piano 0:4, Fingered Bass 0:33, kit Brush 128:40, Mellow Grand Piano 8:0 | Marimba 0:12, Strings Pizzicato 0:45, Picked Bass 0:34, kit Standard 128:0, Glockenspiel 0:9; en el final, Strings Fast 0:48 | Synth Bass 1 0:38 (pulso), Fingered Bass 0:33, Warm Pad 0:89, Celesta 0:8, kit Room 128:8 |
| Melodía | piano suave desde el compás 5 | glockenspiel desde el compás 5 | celesta desde el compás 3, motivo que queda abierto |
| Final | Fmaj9 | Do mayor con platillo, cuerdas sostenidas y trémolo de marimba (21-nov-2026: el final anterior caía a -45 dBFS a los 1.6 s) | La menor con novena |

Proceso de cada cama (`componer_camas.py`): la partitura se toca una vez en FluidSynth (sin reverberación ni chorus del sintetizador, interpolación de 7.º orden, un canal por instrumento y el bombo aparte), con 12 s de cola. Cada pista lleva su ecualización, su nivel por sonoridad objetivo y, en la batería, compresión. La reverberación es una convolución con una respuesta sintética (ruido determinista en tres bandas). Lo que suena después del último compás se suma al principio, así que el loop es circular por construcción; luego van una saturación suave (tanh) y un limitador de pico real en modo circular. El loop queda en -16 LUFS y -4 dBTP; `genvid.py` sube la mezcla a -14 LUFS.

## Los efectos

`sintetizar_sfx.py`: osciladores, ruido determinista y filtros; sin samples. Cada uno empieza y termina en cero y tiene pico de -3 dBFS; su nivel en la mezcla está en `SFX` de `genvid.py`.

| Efecto | Cómo se hizo | Nivel en la mezcla |
|---|---|---|
| whoosh | ruido con un pasabanda que barre de 280 Hz a 1.8 kHz y baja a 900 Hz, con paneo de izquierda a derecha | -6 dB |
| pop | seno que cae de 1050 a 430 Hz en unos 12 ms, con un armónico y un clic filtrado muy corto | -3 dB |
| tick | senos amortiguados de 1450 y 720 Hz (6 y 11 ms) y un toque de ruido; centro en ~930 Hz | -12 dB, alternando 0, -2, -1 y -3 dB |
| trazo | ruido en un pasabanda de 1.3 a 2.1 kHz con textura de grano, 0.34 s | -6 dB |
| subida | cuatro senos que suben dos octavas (220 a 880 Hz) más ruido que sube, en crescendo | -6 dB |
| golpe | cuerpo grave que cae de 130 a 62 Hz, golpe de fieltro filtrado y dos parciales suaves (Do5 y Sol5) | -10 dB |

## Mediciones (objetivas)

| | A | B | C |
|---|---|---|---|
| Sonoridad / pico real | -16.0 LUFS / -4.0 dBTP | -16.0 / -4.0 | -16.0 / -4.0 |
| Tempo por autocorrelación de ataques | 89.98 BPM | 111.98 BPM (mide 55.99, la mitad) | 98.02 BPM |
| Cuantización (R; al azar sería ~0.06) | 0.997, desfase 0.6 ms | 0.993, desfase 0.2 ms | 0.997, desfase 1.1 ms |
| Banda 2 a 5 kHz contra 500 Hz a 1 kHz | -10.7 dB | -7.2 dB | -9.9 dB |
| Octava de 250 Hz contra la de 125 Hz (lodo) | +1.1 dB | -3.0 dB | -5.5 dB |
| Debajo de 30 Hz contra 63-125 Hz | -32.3 dB | -30.5 dB | -32.5 dB |
| Correlación estéreo debajo de 150 Hz | 1.00 | 1.00 | 0.97 |
| Unión del loop: agudos contra los demás inicios de compás | -0.2 dB (mediana) | +2.6 dB (mediana), 0.0 (máximo) | -0.7 dB (mediana) |
| Silencios de 50 ms bajo -50 dBFS / muestras saturadas | 0 / 0 | 0 / 0 | 0 / 0 |
| Limitador del loop | 1.95 dB en picos aislados | 1.76 dB | 2.94 dB |

En B, los agudos solos dan R = 0.80: el shaker tiene un ataque lento y el detector lo marca unos 20 a 30 ms tarde. Las notas salen de una partitura cuantizada, y los medios de B dan R = 0.997.
