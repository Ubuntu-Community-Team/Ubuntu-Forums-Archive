---
title: "Mounting partitions"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Ajay Ramaseshan on 2008-02-06
Hi
By mistake I mounted my Lnux partiton /dev/sda3 on to the folder /media while acting 
as superuser....Now when I try to unmount the partition using command umount /dev/sda3

it gives an error ---

umount: /: device is busy
umount: /: device is busy

What should I do??

Can I just go to /media and exeute rm -R * ?? Will that work???

---

### Post by edwardLS on 2008-02-06
Two things that I can think of that may help.

1. Make sure that the cwd (current working directory) is not in /media/sda1, and

2. You may have to "sudo" the umount command.

Good luck.

---

### Post by dgray_from_dc on 2008-02-06
> **Ajay Ramaseshan said:**
> Can I just go to /media and exeute rm -R * ?? Will that work???

**DO NOT USE THAT COMMAND!!!!!**   You will delete everything on your disk.

The rm command  has nothing to do with mounting or umounting a volume.

> **Ajay Ramaseshan said:**
> umount: /: device is busy

It's telling you that you are trying to unmount your root file system.  This is impossible as it is busy running the OS.

Have you tried rebooting?

---

### Post by bwtranch on 2008-02-06
Re #3 This is true. You can't unmount a filesystem that is busy. But, you can do a workaround with a live cd.

---

### Post by Ajay Ramaseshan on 2008-02-24
I tried to rebbot the system and it worked the Linux partition /dev/sda3 got unmounted....
Thanks a lot for the help.

Ajay

---

