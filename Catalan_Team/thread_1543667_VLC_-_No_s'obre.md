---
title: "VLC - No s'obre"
date: 2010-08-01
forum: Catalan Team
---

### Post by tanreb20 on 2010-08-01
Hola!

Fa uns dies que quan intento obrir aquest programa es queda "adormit" i no hi ha manera...

Quan l'executo desde terminal em salta molts errors, i no els entenc:

```
[501][alorma:/home/alorma]$ vlc
VLC media player 1.0.6 Goldeneye
[0x9a73ad8] main libvlc error: no memcpy module matched "any"
[0x9b4cd88] main access error: no access module matched "file"
[0x9b4c120] main input error: open of `file/xspf-open:///home/alorma/.local/share/vlc/ml.xspf' failed: no access module matched "file"
[0x9b4c120] main input error: No es pot obrir la vostra entrada
[0x9b4c120] main input error: El VLC no pot obrir el MRL 'file/xspf-open:///home/alorma/.local/share/vlc/ml.xspf'.Per a més detalls revisa el registre.
[0x9b4fe58] main interface error: no interface module matched "hotkeys,none"
[0x9b4fe58] main interface error: no suitable interface module
[0x9a73ad8] main libvlc error: interface "hotkeys,none" initialization failed
[0x9b4fe58] main interface error: no interface module matched "inhibit,none"
[0x9b4fe58] main interface error: no suitable interface module
[0x9a73ad8] main libvlc error: interface "inhibit,none" initialization failed
[0x9b4fe58] main interface error: no interface module matched "screensaver,none"
[0x9b4fe58] main interface error: no suitable interface module
[0x9a73ad8] main libvlc error: interface "screensaver,none" initialization failed
[0x9a73ad8] main libvlc error: option drawable-xid does not exist
[0x9b4fe58] main interface error: no interface module matched "signals"
[0x9b4fe58] main interface error: no suitable interface module
[0x9a73ad8] main libvlc error: interface "signals" initialization failed
[0x9b4fe58] main interface error: no interface module matched "globalhotkeys,none"
[0x9b4fe58] main interface error: no suitable interface module
[0x9a73ad8] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x9a73ad8] main libvlc: Ejecutar vlc con la interfaz predeterminada. Usa «cvlc» para usar vlc sin interfaz.
[0x9b4ca68] main interface error: no interface module matched "any"
[0x9b4ca68] main interface error: no suitable interface module
[0x9a73ad8] main libvlc error: interface "default" initialization failed

```

He intentat esborrar-lo i reinstalar-ho, pero no ha funcionat :S

---

### Post by Catalanoic on 2010-09-26
a mi em passava el mateix fins que vaig actualitzar a una versió que em va solucionar el problema.

---

