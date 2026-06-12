---
title: "No puc actualizar KlamAv 0.46"
date: 2010-12-15
forum: Catalan Team
---

### Post by yae7 on 2010-12-15
Hola:

quan intento actualitzar el klamav em sorgeix un error. Com aquest d'aqui: [http://ubuntuforums.org/showthread.php?t=1547713&highlight=update%2Bklamav](http://ubuntuforums.org/showthread.php?t=1547713&highlight=update%2Bklamav) però en el meu cas ja he seguit els passos que proposen i no em funciona.

Si intento actualitzar via consola, em surt:


> Error: "/tmp/kde-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-elmeuusuari" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
QLayout "unnamed" added to Klamav "KlamAV ", which already has a layout
Error: "/tmp/ksocket-elmeuusuari" is owned by uid 1000 instead of uid 0.
elmeuusuari@elmeuusuaripc:~$ Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-elmeuusuari" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-elmeuusuari" is owned by uid 1000 instead of uid 0.

Alguna idea de com solucionar-ho?

salutacions

---

### Post by wgarcia on 2010-12-17
T'està dient que tots aquests fitxers haurien de tenir com a propietari l'usuari "root" i no l'usuari "1000" que deu ser el teu usuari. L'actualització la fas amb "sudo"? Una altra possibilitat és canviar la propietat d'aquests fitxers a root a veure si completa l'actualització:

sudo chown root.root /tmp/kde....

per a cada fitxer que dóna problema.

---

