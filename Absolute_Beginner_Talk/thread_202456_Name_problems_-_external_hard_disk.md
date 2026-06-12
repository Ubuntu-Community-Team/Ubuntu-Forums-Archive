---
title: "Name problems - external hard disk"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-06-23
Hi

This is a trival problem, but it's drviing me nuts and  I'd love to get to the bottom of it.
I've got an external hard disk. It appears happily on my desktop, under the name 'My Book'. That seems reasonable- it's a WD My Book drive.

I can open the drve, copy files to the drive, and unmount  the drive by a right mouse click and selecting 'Eject'. I bought the drive to archive the home folders on my system, and I've managed to do this using 'Archive Manager'. When I use Archive Manger, then the drive appears under the name 'My Book'.

What I can't do, is access this drive using the command line and the My Book name. If I run ls on the media directory, the My Book appears happily in dark blue along with all my other drives. However, when I try cd /My Book, I get the message:

bash: cd: My: No such file or directory

It's almost as though there's some hidden symbol between the 'y' of 'My' and the 'B' of 'Book'.

Anybody any ideas? The whole thing seems a bit daft - the GUI works, but the command line doesn't.

Roger D

---

### Post by aysiu on 2006-06-23
Your book may not be mounted at the top-level directory, so putting a slash in front may not work.

Also, since it's two parts, you need to put quotation marks around it: ```
cd /media/"My Book"
``` will most likely get you there.

To see exactly where it's mounted, try ```
df -h
```

---

### Post by RogerD on 2006-06-23
Absolutely brilliant!

The quotation marks did the trick - many thanks.

---

### Post by Brunellus on 2006-06-23
double quotes will do it, as will the following 

cd /media/My\ Book/

note, that's a BACK slash before the space in "My Book"

---

### Post by carlosqueso on 2006-06-23
or you can probably type
cd /media/My
and press tab, which SHOULD complete it for you if you don't have another drive beginning with My.  I love tab completion :-D

---

### Post by RogerD on 2006-06-23
Many thanks to everyone for all these helpful suggestions. Ubuntu and the Ubuntu Forums are just great

---

