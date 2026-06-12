---
title: "Confused about vfat"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-09-22
I am confused as to how to format my external hard drive to vfat. I want to share the drive with linux/windows/and mac users so I want a file system that they can all share. 
I currently have fat32 but hear that it has become out shined by vfat. The problem is that I do not have a vfat option in gparted.

---

### Post by Pumalite on 2007-09-22
At the Terminal:

mkfs.vfat /dev/xxx
(xxx to be replaced by you according to your device)

---

### Post by cwrann on 2007-09-22
thank you, is vfat a completely different filesystem or is it some sort of extension of fat32?

---

### Post by yabbadabbadont on 2007-09-22
It is just another name for fat32.

---

### Post by Pumalite on 2007-09-22
It's in the same family. They claim it's more advanced. I have never used it.

---

### Post by cwrann on 2007-09-22
yabbadabbadont, is vfat the same as fat 32?

when I enter 
```
mkfs.vfat /dev/sdb1
```

I get

```
bash: mkfs.vfat/dev/sdb1: No such file or directory

```

---

### Post by cwrann on 2007-09-22
Nevermind the code from the first one I was missing a space heres what I get now:

```
home@home-desktop:~$ mkfs.vfat /dev/sdb1
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: /dev/sdb1 contains a mounted file system.

```

---

### Post by Pumalite on 2007-09-22
You have to unmount sdb1 before formatting.

---

### Post by cwrann on 2007-09-22
under the properties of the hard drive it says that the file system is VFAT (fat 32).

Are they the same? Is this why gparted only gives you the option for fat32?

---

### Post by Pumalite on 2007-09-22
I wouldn't worry and go with Fat32

---

### Post by cwrann on 2007-09-22
Apparently I have vfat on the hard drive even though gparted calls it FAT32. now I'm just curious if there is a difference or not? There is a lot  of confusion in the posts that I have read about it.

---

### Post by cwrann on 2007-09-22
I went to wikipedia and I think I get it now. vfat is an extension that is added to the FAT filesystems to allow long file names. I think that you can have a vfat (FAT16) or a vfat (FAT32). I guess gparted automatically gives you the vfat extension and therefore just calls it FAT16 and FAT32.

Let me know if I am wrong.

---

### Post by Pumalite on 2007-09-22
[http://tldp.org/HOWTO/Flash-Memory-HOWTO/basics.html](http://tldp.org/HOWTO/Flash-Memory-HOWTO/basics.html)

---

### Post by cwrann on 2007-09-22
Thanks for the link. I gather from what I read there that nowadays FAT filesystems are all considered vfat. I don't think many peopel realize this as I have been told in the past to change my FAT32 filesystem to the superior vfat.

---

### Post by Pumalite on 2007-09-22
You are welcome. Happy Ubuntuing!

---

