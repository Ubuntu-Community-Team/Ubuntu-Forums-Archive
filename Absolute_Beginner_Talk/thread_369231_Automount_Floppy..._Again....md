---
title: "Automount Floppy... Again..."
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Januszad on 2007-02-24
Hi!

I am using ubuntu 6.12.
I would like to automount floppy...

i have tried several how to's including pmount, autofs and it is still not working.

Can anyone explain me step by step how to make floopy automount??? PLEASEEEEEEEEEEEE!!

Thanks in advance,

Regards Janusz

---

### Post by chggr on 2007-02-24
Insert a floppy into your drive, click "Places" -> Computer -> Floppy.
It should now start reading the floppy drive and mounting it automatically.

If this doesn't work, check that your /etc/fstab file contains the following line:
/dev/fd0        /media/floppy  auto         rw,user,noauto     0       0

PS: If you mean that you want the drive to mount by itself when you insert a floppy without you doing anything, then I'm afraid this is not possible. Floppy drives cannot sense the presence of a medium inside them, so they cannot mount by themselves like USB devices do for example.

---

