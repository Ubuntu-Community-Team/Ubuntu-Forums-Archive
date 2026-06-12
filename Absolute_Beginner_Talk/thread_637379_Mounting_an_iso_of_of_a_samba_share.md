---
title: "Mounting an iso of of a samba share"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by BodaciousBrian on 2007-12-10
Ok so i've tried this server different ways and none are working.

sudo mount -t iso9960 -o loop /media/server/software/games/diablo_2/install.iso /media/mount0

/media/server/software/games/diablo_2/install.iso: Permission denied

this is the only one of 3 methods that are giving me an error, the other two, an iso mounting script and gmount-iso, pretend like it worked fine.. I'm using sudo, so i don't see how permission is denied.

Also /media/server is a mount from a smbfs share.

(and I do own this game, im just one of thoes that hates switching CD's :))

---

