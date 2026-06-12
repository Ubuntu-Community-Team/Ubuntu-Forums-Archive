---
title: "ubuntu installed want xp"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by ochana25 on 2008-01-26
hey everyone i have ubuntu installed on my pc right now and i wanted to install xp but i dont wanna run them at the same time i wanna choose either one at system startup how do i go abouts of doin this thanku

---

### Post by st33med on 2008-01-26
You actually want to install XP first because the installation is going to overwrite the entire disk. THEN install ubuntu via dual boot.

---

### Post by Dr Small on 2008-01-26
As my good pal st33med recommended, try installing Windows XP first, and then Ubuntu last. Grub will sort out the OS entries, and then you can pick and choose which OS you want to boot.

It will work that way ;)

Dr Small

---

### Post by Flyingjester on 2008-01-26
right, i would recommend installing xp first, partitioning enough room for ubuntu, then installing that second, makes dual booting very simple, as grub will automatically recognize your windows partition.

---

### Post by rleechb on 2008-01-26
Don't mean to hijack, but is there anyway to make grub boot windows by default (making it the 1st selection in the boot screen, instead of ubuntu)?

---

### Post by st33med on 2008-01-26
rleechb, that is kinda a long answer. You might need to put that in another thread.

---

### Post by Kilz on 2008-01-26
> **rleechb said:**
> Don't mean to hijack, but is there anyway to make grub boot windows by default (making it the 1st selection in the boot screen, instead of ubuntu)?

The search feature is our friend.

---

### Post by Gazneth on 2008-01-26
If your Ubuntu is installed already and you have a free or unpartitioned space on your drive, I believe you can install XP. After you complete the install run the SuperGRUB disk which will fix your bootloader to allow you to choose from either OS.  SuperGrub can be downloaded from the Internet. Always have a backup of your files before attempting something like this. Worst case will have you restoring a Ubuntu backup to a partition, after the XP install. Then a supergrub  to fix bootloader

---

### Post by ochana25 on 2008-01-26
i might of done it wrong but i had xp installed first then i click install on the ubuntu and it overwrote everything.

---

### Post by Parmenion on 2008-01-26
If you are doing a dual boot installation, you have to use the manual partitioning process. The reasoning is that the default paritioner simply takes over the full drive, nuking all other partitions in the process.

Have fun

---

### Post by pollywog on 2008-01-26
Well, yep you messed up. I'd start over with the XP install, hopefully you didn't  do too much setting up of that system. So let XP install over the whole disk. After that,  I'd recommend that you get your hands on a decent partition editor. Gparted can be freely downloaded at:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Burn it to a disk, then boot off of it *after you install XP*. You can then shrink the NTFS partition, till you have enough room for you Ubuntu partitions (2). Leave the area of the disk that you're installing Ubuntu on unpartitioned. When you get to the part of the Ubuntu install where it asks you where you want to install Ubuntu, choose the *install on largest continuous free space* option. That should give you a good dual boot. While you are editing your partitions with gparted, you might want to set up another partion as either fat32, or better ext3, and use it as data storage  for both systems. If you  use ext3, you can get a program to allow windows to use a linux partition at:

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

and a tutorial of how to mount this volume on your Ubuntu system at:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

