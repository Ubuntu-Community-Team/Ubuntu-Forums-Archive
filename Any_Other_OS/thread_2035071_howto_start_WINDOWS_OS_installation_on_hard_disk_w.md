---
title: "howto start WINDOWS OS installation on hard disk with grub2"
date: 2012-07-29
forum: Any Other OS
---

### Post by funicorn on 2012-07-29
If one wants to install WINDOWS OS but get no cd drive or it's broken, ,  if he has a MSDN WINDOWS image downloaded,  and has grub2 installed on disk, then this post would help. Ignore it if u don't like it.

All starts from a new feature introduced in grub2, that can activate the windows boot script called bootmgr, with following commands:
```

grub:> set root=(hdX,Y)  #where bootmgr is located.
grub:> insmod ntfs # load ntfs module
grub:> ntldr /bootmgr
grub:> boot
```So that one can start  windows on-disk installation from a grub-shell.

1. Mount the windows image: the iso file

2 copy all files and dirs in the iso file to the root of  a ntfs partition #not any directory

3 reboot, enter grub2 shell, type in the above commands.

4 then you will see the windows installation starting.

Tips:

a. If u are not sure about the the number of partition where bootmgr is located, u can use this trick:
```
grub:> search --file --set=root --no-floppy /bootmgr
```This will auto set the target partition as root.

b. The latest microsoft windows images  likely use udf filesystem, when mounting, remember to use '-t udf' option.

---

### Post by uRock on 2012-07-29
Not an ubuntu support request. Moved to ***Other OS/Distro Talk***.

---

### Post by Rutr on 2013-05-25
What about with more windows installation? eg. Windows XP, Windows7, Windows8 x86 and Windows8 x64 on ONE partition. Is it possible?

---

### Post by uRock on 2013-05-25
One hard drive, yes. One partition, no.

---

### Post by Rutr on 2013-05-26
I meant to create multiple Windows installers on one partition. With other OS i can boot installers from iso file, but i can't boot windows installation discs. Is it possibility to boot windows installation from iso file? Sorry for my bad English.

---

### Post by uRock on 2013-05-26
You would probably be better off asking such questions on a Microsoft website.

---

### Post by Rutr on 2013-05-26
Is it posible to boot winsows installers from grub2 on one partition?

---

