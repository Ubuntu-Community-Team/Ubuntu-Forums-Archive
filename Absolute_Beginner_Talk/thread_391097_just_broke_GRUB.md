---
title: "just broke GRUB"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by dracomordag on 2007-03-22
i deleted my ubuntu installation so that i could reformat my drive, set up partitions, etc.

i left my original XP NTFS-based partition (30 GB)

now, when i boot, i get the following:

Initializing Intel(R) Boot Agent Version 4.1.06
PXE 2.1 Guild 083 (WfM 2.0), RPL v2.74
GRUB Loading stage1.5.


GRUB loading, please wait...
Error 15





what do i do now?

my current plan is to just install Ubuntu again through the live CD and hope it fixes everything.

---

### Post by gameman12 on 2007-03-22
this means grub can't find it's files to properly boot.

go to the link and use the super grub disk. it shouldh help fix grub and get u up and running again

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

if u want u could reinstall with the live cd if u want to keep ubuntu as well but try the SGD first

---

### Post by Henry Rayker on 2007-03-22
I'm not certain, but I believe that GRUB is looking for its configuration file /boot/grub/menu.lst. Basically, what is happening is that Grub is installed on the MBR, when you start the machine, it starts GRUB, which then looks for the menu.lst...it's not there, so it throws a nasty error.

Depending on what you want to do, your next course of action could be different:
1) If you need to get into Windows to do something before you reinstall Ubuntu, you will need your Windows cd and use the fixmbr command
2) If you don't need to get into Windows, you can just reinstall Ubuntu and set up the partitions accordingly.

I hope that made sense. Let me know if I can clarify.

---

### Post by dracomordag on 2007-03-22
i dont need to do anything in windows, but when i try to install ubuntu, i get the following error:

"No root file system is defined.

Please correct this from the partitioning menu"


my tree is defined as follows:
```
+/dev/hda
|- /dev/hda1 ntfs /media/hda1         31453MB
|- /dev/hda2 ext3 /media/hda2 format? 8389MB
|- /dev/hda4 ext3 /media/hda4 format? 39234MB
|- /dev/hda5 swap                     921MB
```


EDIT: i think i got it... just change the "/media/hda2" to "/", right?

and i can also change /media/hda4 to /home, removing the need for [this](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by Henry Rayker on 2007-03-22
In the partitioner, you have to set hda4's mountpoint (I'm assuming that you want the larger ext3 partition to be for Ubuntu) as '/'

To do this, you have to define your own partition table (the default I believe looks for empty space but, because there is none, it can't define a root partition it whines about it.

---

