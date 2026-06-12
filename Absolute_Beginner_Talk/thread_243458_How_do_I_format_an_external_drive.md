---
title: "How do I format an external drive?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-08-25
In windows I just right click and hit format, but there seems to be no such option here. And I'd also like to be able to choose what it gets formatted to. 

In this particular case, I'm hoping to get an SD card formatted to FAT.

---

### Post by bullgr on 2006-08-25
to format a drive you need the "mkfs" command
open a terminal and type
> man mkfs
to see the options
for example to format my internal second hard disk first partition in reiserfs "hdd1" i use the command like this:
> sudo mkfs.reiserfs /dev/hdb1
another example... external hard disk first partition fat32:
> sudo mkfs.fat32 /dev/sda1

note: be sure how is named the disk you need to format. look at /dev folder... it's important, you don't will to format wrong disk :mrgreen:

---

### Post by amo-ej1 on 2006-08-25
the best way is to simply insert the sd card and look at the output from the 'dmesg' command this will show the kernel messages including the detected partitions and the size of the disk but also the device name that gets allocated to the device. You can use this devicename in commands mentioned in the post above.

---

### Post by anaconda on 2006-08-25
I would install qtparted, and use it. qtparted has easy graphical interface..

---

### Post by tnf on 2006-08-25
or gparted, which looks nicer in my personal opinion

---

