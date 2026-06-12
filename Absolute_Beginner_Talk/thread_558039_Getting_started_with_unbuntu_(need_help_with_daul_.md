---
title: "Getting started with unbuntu (need help with daul booting)"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by OnlyHuman on 2007-09-23
alright so here we go...

i have just learned about unbuntu linux like three days ago and decided why not because if i accidentally mess up my computer i can always clean wipe because theres nothing important on it.
so i have two internal hard drives that i can easily access becuase i have no cover on the case one is a 170 gigabyte hard drive with a geniune copy of windows xp proffessional service pack two and a 30 gigabyte hard drive that is empty now i want to install unbuntu onto the 30 gigabyte harddrive as a slave  drive although i have no idea how to install unbuntu onto the second hardrive and no idea how to go about daul booting i at one time was going to make a daul boot system with xp and vista but i found out that i hated vista so if anyone could refer to me a tutorial guide or just explain it in a reply i wouldbe thankful

---

### Post by forestpixie on 2007-09-23
have a look at [this]("http://www.psychocats.net/ubuntu/installing") it should help you out - good luck with it

---

### Post by Yes on 2007-09-23
First, burn a copy of the Ubuntu live CD.  Boot from the CD (You might have to change the BIOS settings to boot from a CD first), and then install Ubuntu.  There should be an option to change what hard drive you partition, make sure you chose the 30 GB hard drive.  It should install GRUB for you on the 30 GB hard drive, and when you restart your computer after installing Ubuntu, you'll see a GRUB menu that will give you an option of booting between Ubuntu and Windows.  If you get any errors with GRUB, don't freak out.  They're fairly common when dual booting, and very easy to fix (You normally just have to switch some numbers around in some config files).

Also, make sure you have a working copy of your Windows disk, incase you overwrite the Windows MBR.  Again, it's an easy fix, as long as you have the disk.

Good luck.

---

### Post by Pumalite on 2007-09-23
Using Live CD or Alternate CD? Either one: choose sdb (2nd drive), Gided>Use Entire Disk.

---

### Post by ukripper on 2007-09-23
Also check this guide for later use - [https://help.ubuntu.com/community/Beginners/Guide/Feisty](https://help.ubuntu.com/community/Beginners/Guide/Feisty)

---

### Post by OnlyHuman on 2007-09-23
where would i get the unbuntu linux files to burn onto a cd

---

### Post by Pumalite on 2007-09-23
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Maestro23 on 2007-09-23
> **OnlyHuman said:**
> where would i get the unbuntu linux files to burn onto a cd

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

