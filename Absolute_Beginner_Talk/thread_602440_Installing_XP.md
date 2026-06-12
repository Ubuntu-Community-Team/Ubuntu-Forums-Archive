---
title: "Installing XP"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Bheegerji on 2007-11-04
I installed Ubuntu 7.10 and found some hardwares were not supported. So, I decided to install Win XP again along with Ubuntu as a dual boot. I read through many posts and found that dual boot of XP is not possible after Ubuntu is installed. So I've to install XP and then Ubuntu to get a dual boot. I inserted the Win XP CD into my drive and restarted my system but Win XP din boot. I'm forwarded to Ubuntu again.

How do I install XP again??

---

### Post by Pumalite on 2007-11-04
Get Gparted Live CD [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it and make a partition for XP at the beginning of the drive, formated ntfs. The rest format ext3 if you want. Then install Xp. Then install Ubuntu.

---

### Post by Stefanius on 2007-11-04
eyey,

You have to split your harddrive, the best thing is, to setup XP first.

On your patition (C:)you will setup XP. Before you do this you can create 3 partition in the partition manager of the XP disc:

-one formated as NTFS (drive C)
-one unformatetted
-one unformatted and the size has to be twice as your RAM (SWAP-partition)

setup XP as you always (note: It's not recomended to use a tool like PArtition Magic after your XP instalation, it really messed up some things)

When you setup Ubuntu you must choose for a Manual-partition setup (dont know the real name of that option, but you will see it if you there)  and choose the 2 partitions you created before. Continue tje setup as you always do.

and...

Trlalalaaala, your dualboot is finisch (everytime you start your PC, you get the Grub-loader so you can choose you OS)

Stef.

---

### Post by damotor on 2007-11-04
Once you've got both operating systems installed you have to set up grub in order to let you run windows, look for the tool in the system menu

---

### Post by Rabindranath on 2007-11-04
You need two files 'boot.ini' and 'ntdelect.com' for your windows cd to boot and you should have an ntfs or fat32 partition.. If you have removed XP then the 2 files would have gone. My advice to you is to install XP and either reinstall ubuntu or reinstall its grub through the live cd. I think you could use gparted live.

---

### Post by ddrichardson on 2007-11-04
Are you sure you have a bootable XP disk? It's not an upgrade disk or such like.

---

### Post by Bheegerji on 2007-11-27
How to install the grub from the live cd? What's the name of the file that I've to install.

---

