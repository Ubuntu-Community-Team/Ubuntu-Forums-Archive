---
title: "floppy - totally confused"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-01-07
i've tried a number of things that i have found in the forums, including installing some 'pmount' thing, and i get the error below when i right click on 'floppy drive' and select 'mount volume.

Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount

i'm going to try to do this [http://www.debian.org/ports/netbsd/](http://www.debian.org/ports/netbsd/) on an NEC vesta v/50. (it's either that, or clean off the driveway.)

---

### Post by fuscia on 2006-01-07
problem solved. did...

*sudo gedit /etc/fstab*

under floppy0, changed 'auto' to 'vfat' and saved the change

then *sudo mount /media/floppy0* and it showed up in nautilus.

---

### Post by randlieb on 2006-01-14
[QUOTE=fuscia]problem solved. did...

*sudo gedit /etc/fstab*

under floppy0, changed 'auto' to 'vfat' and saved the change

then *sudo mount /media/floppy0* and it showed up in nautilus.[/QUOTE]

HALLELUJAH!!!!
couldn't read a floppy in breezy. looked through several threads and this is the post that got it to work!!!!! THANKS. it put a FLOPPY icon in the PLACES menu. insert my floppy, click on the icon and voila, floppy is read.

---

### Post by tastyturkey on 2006-02-09
but have you tried writing to the floppy?

with the solutions given on this forum I can mount floppies but not write to them

---

### Post by StefanoCole on 2006-02-10
tastyturkey, to write to the floppy do the following:
sudo gedit /etc/fstab
In file fstab add the following line if not already present:
/dev/fd0   /media/floppy0   vfat   [COLOR="Red"]rw[/COLOR],user,noauto    0    0

Stefano

---

### Post by randlieb on 2006-02-10
have no problem copying to and from floppy. just looked at fstab again and see that RW is already there.

---

### Post by judesoul on 2006-06-06
thanks fucia...iut works for me! :)=D>

---

