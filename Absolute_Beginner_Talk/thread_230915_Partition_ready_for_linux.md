---
title: "Partition ready for linux"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by wideboy on 2006-08-06
Hi all

I am a complete P.C novice even though I am a computer programmer 

I have my discs on order to put ubuntu Linux on my p.c. 

Do I need to partition my hard drive first? If so how much gig and how? I have partition magic but have not yet installed it.

I primarily want Linux for a LAMP set up. I want to learn apache/myslq/php for my web pages.(and to put on my C.V)

The wife also uses the P.C. and has her own account would the install affect this? I also have no windows xp back up disks. Time wanted 50 quid when I brought the P.C so i did not bother. Do I need to do a back up somehow?

Thanks in advance, first for reading this and second for any answers.

Regards

wideboy

---

### Post by fene on 2006-08-06
yes, you will have change your partion table in order to install linux on your computer. if you have just one harddisk in your computer the setup program for linux will try to create a partition (actually two partitions, one to install the operating system to, and one swap partition).

if you don't have any unpartitioned space on your harddisk and you don't want to delete your win xp partion(s) you'll need partition magic (or something similar) to resize an existing partition in order to get space for the linux partitions to create. but be carefull with partion magic. i once ****** up my whole master boot record (mbr) with this tool.

For sure it's recommended to do a backup of your data. Playing around with partions is something that could end in a disaster, if you're not sure what to do.

it's no problem to run windows and linux on the same machine. linux will install "grub", a boot manager that allows you to select the OS the boot every time you start your computer.

good luck!

---

### Post by Jagot on 2006-08-06
You may want to read this with regards to a LAMP installation:

[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

You do not need to partition the drive first.  Ubuntu's installer can handle that.  Do not use Partition Magic.  Ubuntu's partitioner can handle the resizing of your current Windows partition so Ubuntu can fit on there.

Use however much space you want.  You'll need to install the ubuntu-desktop package so you have a GUI, so the minimum requirment for that is really oing to be 3GB.

You can have as many user accounts as you like so you can set up one your wife.

If you have any data that is at all important to you on the computer then back it up.

---

