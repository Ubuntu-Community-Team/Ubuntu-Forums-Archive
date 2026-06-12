---
title: "No Root File System Defined....I'm extremly new at this..."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by nightynight on 2007-11-11
Ok, so i just started with this whole Linux thing and i'm trying to install it without deleting windows..So i partitioned my hard drive like so:

dev/sda1/                 ntfs   PQSERVICE
dev/sda2/ (Locked)  ntfs   /media/ACER          <---This partition has Windows on it.
dev/sda3/                 ntfs   DATA
dev/sda4/                 ntfs                                  <---This partition is the one I'm trying to install Ubuntu on.

And when i try installing Ubuntu I get the error message "No Root File System Defined".

So please tell me how to fix this...and in steps or dumb speak if u can...im really new at this...

Thanks muchly!!:)

---

### Post by Pumalite on 2007-11-11
You have to give a mount point to '/'

---

### Post by matthewcraig on 2007-11-11
Welcome to the Ubuntu community.  You will need multiple partitions to install Linux: a root and a swap partition, at least.  Also, a seperate /home partition is very useful, for your personal data.

---

### Post by nightynight on 2007-11-11
Thanks for the info...and the welcome!

err...

how would i give a mount point? lol....i feel so noob.

---

### Post by Sef on 2007-11-11
> dev/sda4/ ntfs <---This partition is the one I'm trying to install Ubuntu on.

You need to use the default file system in Ubuntu, which is ext3.   Ubuntu will not install to NTFS as it is proprietary.

---

### Post by nightynight on 2007-11-11
ok, but still would i need to give a mount point?  And how would i do that with the Ubuntu Live CD GParted?

---

