---
title: "alsa a 10.04: problema de biblioteques??"
date: 2010-09-15
forum: Catalan Team
---

### Post by marteljorge on 2010-09-15
Resulta que no em va l'àudio al portàtil i tampoc al servidor. En ambdós tinc l'Ubuntu 10.04 i al portàtil he mirat d'actualitzar els paquets d'ALSA a la versió de Debian Sid. He tocat la configuració d'ALSA i ara el portàtil detecta la tarja. Tot i això, segueix sense funcionar.
```
root@ubuntu:~# espeak Hola.
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

```
I amb el mplayer sembla que reprodueix, però el resultat és cap àudio a les sortides. No adjunto el fitxer que m'ha fet l'alsa-info.sh perquè pesa massa. [http://http://pastebin.com/Gs56kj2G](http://http://pastebin.com/Gs56kj2G)

---

