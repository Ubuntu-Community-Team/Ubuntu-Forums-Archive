---
title: "Howto create a bootable OpenBSD install CD"
date: 2007-09-19
forum: BSD
---

### Post by mips on 2007-09-19
Ok, if you don't have money or can't wait for your cd to be delivered to you then you can make your own.

These instructions are for OpenBSD 4.1 i386 arch.

Open a terminal:
```
[COLOR="Silver"]mips@obelix ~ $[/COLOR] cd /tmp
[COLOR="silver"]mips@obelix /tmp $[/COLOR] mkdir -p OpenBSD/4.1/i386
[COLOR="silver"]mips@obelix /tmp $ [/COLOR]cd OpenBSD/4.1/i386
[COLOR="silver"]mips@obelix /tmp/OpenBSD/4.1/i386 $[/COLOR] wget ftp://ftp.openbsd.org/pub/OpenBSD/4.1/i386/*
[COLOR="silver"]mips@obelix /tmp/OpenBSD/4.1/i386 $[/COLOR] cd ../../
[COLOR="silver"]mips@obelix /tmp/OpenBSD $[/COLOR] mkisofs -v -r -T -J -V "OpenBSD41" -b 4.1/i386/cdrom41.fs -c boot.catalog -o OpenBSD41.iso /tmp/OpenBSD/
[COLOR="silver"]mips@obelix /tmp/OpenBSD $[/COLOR] ls -l
total 228740
drwxr-xr-x 3 mips root      4096 2007-09-19 08:14 4.1
-rw-r--r-- 1 mips root 233990144 2007-09-19 08:21 [COLOR="Red"]**OpenBSD41.iso**[/COLOR]
[COLOR="Silver"]mips@obelix /tmp/OpenBSD $[/COLOR] md5sum OpenBSD41.iso
**6f9da8e42d4c0953364624c55733793b ** OpenBSD41.iso

```

Now burn the image to disc with your favourite burner !

---

### Post by Bachstelze on 2007-09-19
And for those who want to run the 4.2 development version (for example because, like mine, their nvidia card is relatively new and requires Xorg 7.2), a full installation ISO is available at :

[ftp://ftp.openbsd.org/pub/OpenBSD/snapshots/i386/install42.iso](ftp://ftp.openbsd.org/pub/OpenBSD/snapshots/i386/install42.iso)

---

