---
title: "Having Ubuntu with my older OS on the same computer"
date: 2005-07-02
forum: Absolute Beginner Talk
---

### Post by pat_togo on 2005-07-02
Hi All,
I have just installed Ubuntu and can't access my other drives (should be Ubuntu on C, WIndows on D, my files on E etc.). Is there a way to have both OS and a choice when booting?
Otherwise if I have to redo the installation of both OS, in which order should I do it, and to what should I pay attention to in order to enable dual booting and access to all drives no matter the OS in use.
Thanks.
Patrick

---

### Post by aysiu on 2005-07-02
I'm assuming your E partition with files is formatted as FAT32 and not NTFS (otherwise, Linux will not be able to safely modify these files):

[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

When you installed Ubuntu, it should have added a Windows boot option, but you can always do this:

[http://ubuntuguide.org/#addwindowsentrygrubmenu](http://ubuntuguide.org/#addwindowsentrygrubmenu)

Ubuntu Guide is your friend... or should be.

---

### Post by poofyhairguy on 2005-07-02
[QUOTE=pat_togo]Hi All,
I have just installed Ubuntu and can't access my other drives (should be Ubuntu on C, WIndows on D, my files on E etc.). Is there a way to have both OS and a choice when booting?
Otherwise if I have to redo the installation of both OS, in which order should I do it, and to what should I pay attention to in order to enable dual booting and access to all drives no matter the OS in use.
Thanks.
Patrick[/QUOTE]


Well....the other poster tells you how....but I must say because a friend of mine did it....are you sure you didn't install ubuntu OVER your old OS? Because teh only way to fix that is to reinstall the old OS.

---

### Post by aysiu on 2005-07-02
I just re-read the post, and I'm with you, Poofy. Ubuntu's installer is great, but the partitioning part can definitely be confusing for a new user. Keep track of your partitions, and make sure you install Windows *first*, then Ubuntu. Ubuntu *should* recognize your Windows drive and autoconfigure a dual boot if you put grub on the MBR.

---

### Post by pat_togo on 2005-07-03
Hi all,
Thanks for the reply. I am definitely sure not having installed Ubungu over Windows. As I said I installed first Windows on D and let the C drive free for Ubungu. I remember having some problems when installing the "grub" (what is that anyway), maybe that's where the problem comes from because maybe this section failed.
I will try my chance again anyway.
Patrick

---

