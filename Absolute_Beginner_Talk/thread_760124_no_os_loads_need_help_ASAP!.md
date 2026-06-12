---
title: "no os loads need help ASAP!"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by privaterolf on 2008-04-19
I was trying to format my iPod to ext2 so I could run iPod Linux.

I open up Gparted, select to format the whole iPod to ext2.

I hit apply, error comes up, so I re-boot my system.

GRUB doesn't load, and I can't get any OS to load.

Help?

btw: I have a Ubuntu 8.04 Live CD

---

### Post by master5o1 on 2008-04-19
If you were using the live CD your main drive might not have been mounted, it is possible you formatted the wrong drive instead of the ipod. Do you remember what the error said? That's probably the most important part.

If you load the Live CD again can you post the output of fdisk -l (best with your ipod in I suppose)

Does your ipod start or has it been wiped.

---

### Post by privaterolf on 2008-04-19
The iPod loads.

I'm 100% sure I selected the iPod.

Only 8GB device I have.

Looks my whole hard drive was formatted with no OS installed.

Great.  Luckily I have a XP disc so I can re-install.

Installing drivers is oh so fun. T_T

Thanks for your help, though.

edit: I wasn't using the Live CD to format.Maybe the reason it formatted was because I unmounted the Dell Utility Partition?

I dunno. :\

---

### Post by master5o1 on 2008-04-19
did you have multiple partitions on your main drive then?
Gparted can not format a mounted drive. Is the error you getting and the beginning grub being confused or actually that the whole drive has been formatted?

What was the error message?

Also if the ipod loads, you obviously didn't format it.

---

### Post by privaterolf on 2008-04-19
> **master5o1 said:**
> did you have multiple partitions on your main drive then?
Gparted can not format a mounted drive. Is the error you getting and the beginning grub being confused or actually that the whole drive has been formatted?

What was the error message?

Also if the ipod loads, you obviously didn't format it.


Dang it.  I wish I knew that Gparted couldn't format mounted drives.

I booted up Live CD, open up GRUB, it says something to the extent that the filesystem was corrupted.

---

### Post by master5o1 on 2008-04-19
Don't do anything rash then, you quite possibly can restore/recover your data. I would suggest trying something like fsck but I am not 100% sure. If your FS is corrupted maybe it's best to start a new thread or change the title of this one asking for help on recovering a corrupted FS.

Still no idea what the error message was from gparted?

---

### Post by privaterolf on 2008-04-19
Nope.

I think it's too late to recover though. :\

I already started formatting my hard drive to NTFS to install Windows XP.

---

### Post by master5o1 on 2008-04-19
No doubt it is too late then. Good luck with getting everything set up again :)

---

