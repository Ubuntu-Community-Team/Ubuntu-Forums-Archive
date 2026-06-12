---
title: "can i put xp on ext3 with ubuntu"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by jryprt on 2007-08-16
I installed ubuntu & wiped my xp ( i did back up ) can i put xp on the ext3 with ubuntu 
do i used gparted ? say with ext3 or go back to ntfs ? 
thanks jerry

---

### Post by diatribe on 2007-08-16
xp needs ntfs, it wont work on an ext3 partiton

---

### Post by diatribe on 2007-08-16
also if you install xp after ubuntu it will remove the ability to boot into linux and you will have to reinstall grub

---

### Post by jryprt on 2007-08-16
should i wipe the drive & install xp than ubuntu

---

### Post by StephUb on 2007-08-16
Hi,

Ubuntu on a ext3
Windows XP on FAT or NTFS

So you need to create a new partition

For the dual boot, you have two choices, windows boot loader or Grub.

---

### Post by diatribe on 2007-08-16
xp and then ubuntu will allow you to dual boot yes

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-16
you dont need to reinstall ubuntu just the grub
wich you can do from the ubuntu live cd 
so partitinon the drive 
then install windows 
then install the grub from ubuntu cd

---

### Post by jryprt on 2007-08-16
gparted will not let me repartion  it is locked thanks jerry

---

### Post by StephUb on 2007-08-16
What disk is locked??
Are you running the GParted from ubuntu or from the live CD ?

---

### Post by diatribe on 2007-08-16
gparted will not let you edit mounted partitons, you need the gparted livecd to do that

---

### Post by jryprt on 2007-08-16
i will try live cd thanks jerry

---

### Post by Tyke91 on 2007-08-16
download the gparted live cd from here

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

use that to edit your partitions :D

---

### Post by Tyke91 on 2007-08-16
errgh... must... read... page.... two ](*,) i always forget to do that

---

