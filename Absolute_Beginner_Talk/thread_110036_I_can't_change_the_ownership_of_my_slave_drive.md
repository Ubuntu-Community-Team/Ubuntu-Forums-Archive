---
title: "I can't change the ownership of my slave drive"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by jenphalian on 2005-12-29
I have a slave drive, FAT32, and I managed to mount it.  There it is on my desktop, hdb5.  This is where I want to be storing all my music and picture files in the future.  For instance, I'd like to be able to rip cds right into that drive, but juicer does not want to do this (when I tell it to extract, it tells me the file is not found).

It seems like the reason I can't put files on my slave drive is a permissions thing, and I'm sure there's some way I could fix this?  I tried -

sudo chown jenphalian:jenphalian /media/hdb5

after reading this forum thread -

[http://www.ubuntuforums.org/showthread.php?t=109999](http://www.ubuntuforums.org/showthread.php?t=109999)

and I got back 'operation not permitted'.


Am I doing something wrong, or going at this from the wrong angle completely?

---

### Post by thekiller on 2005-12-30
try this :

sudo chown jenphalian:users /media/hdb5

---

### Post by jenphalian on 2005-12-30
[QUOTE=thekiller]try this :

sudo chown jenphalian:users /media/hdb5[/QUOTE]

Thanks for the help, but that is also not permitted.

---

### Post by aysiu on 2005-12-30
It's not a chown issue. It's a mounting issue.
See the fourth link of my sig.

---

### Post by jenphalian on 2005-12-30
*reading*  I'll use that tonight, sounds like that will fix my problem.  Thank you!!

---

