---
title: "rhythmbox not working since dapper upgrade"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by no way on 2006-06-27
hello community,

i have exactly the same problem as decribed here: [http://www.ubuntuforums.org/showthread.php?t=164614](http://www.ubuntuforums.org/showthread.php?t=164614).

but only since i upgraded to dapper yesterday...

what could have happened? i don't know where i have to look first.

i am using the amd 64 bit ubuntu version.

my sources.list:
[INDENT][COLOR="Navy"]deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse[/COLOR][/INDENT]


any ideas anyone?
cheers
fred

---

### Post by Brunellus on 2006-06-27
[QUOTE=no way]hello community,

i have exactly the same problem as decribed here: [http://www.ubuntuforums.org/showthread.php?t=164614](http://www.ubuntuforums.org/showthread.php?t=164614).

but only since i upgraded to dapper yesterday...

what could have happened? i don't know where i have to look first.

i am using the amd 64 bit ubuntu version.

my sources.list:
[INDENT][COLOR="Navy"]deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse[/COLOR][/INDENT]


any ideas anyone?
cheers
fred[/QUOTE]
the dapper upgrade breaks existing mp3 support;  to restore it, follow the directions for Dapper at 

[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by no way on 2006-06-28
thanks a lot brunellus, it worked perfectly!!!

fred

---

