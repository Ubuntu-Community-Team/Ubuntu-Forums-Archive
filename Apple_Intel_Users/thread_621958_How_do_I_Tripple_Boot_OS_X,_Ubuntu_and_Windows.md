---
title: "How do I Tripple Boot OS X, Ubuntu and Windows?"
date: 2007-11-24
forum: Apple Intel Users
---

### Post by jincast90 on 2007-11-24
Hello, I own the Santa Rosa based Mac Book Pro. I was wondering if someone can help me/show me a guide in how to tripple boot OS X, Windows and Ubuntu from it?

---

### Post by omax on 2007-11-24
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

Should help you on the way. Just change the partition-sizes as you want it according to your HDD.

---

### Post by ChardFi on 2007-11-24
Please,

Search this forum for "easiest triple boot ever" or anything related. 

Without wanting to sound like a horrible nerd you should really Google your problems and post when you are stuck for an answer.

There is a very useful wiki page on the latest macbooks just search this forum for my lame posts and you will find.

Peace

---

### Post by bonestonne on 2007-11-25
don't be an ***. people post here for help, not people like you.

Boot Camp is the easiest way to triple boot on a Macbook. if you're really up for a challenge, you'll have to base everything in the Grub Boot Loader, and you'll need one hell of a partition table on that drive of yours. I condensed everything, and could probably get away with a 120gb drive doing it, but it would be very sketchy. you'll want at least 250gb to give each OS adequate space for data. XP can't have less than 5gb, Ubuntu cannot have less than 7 i think, for room to install packages and for updates. OS X needs 5.3GB, but you'll need room for updates. Linux also needs a Swap partition. if you have an 80gb drive, you're scraping the boundaries of what's possible.

1) get a copy of G-Parted Live CD
2) Install OS X on partition #1 just use the Disk Manager on the install CD to format the drive.
3) Boot from the G-Parted Live CD. Make the size partition you want for XP, but remember its size, thats most important
4) Install XP. When you do this, install to the exact partition you want. Don't delete or format any other partitions.
5) Install Ubuntu. install Ubuntu to the remaining partition created with G-Parted Live CD. Make sure that you have enough room, and extra for the Swap Partition. This will set up the Grub Boot Loader with Windows XP and Ubuntu on it. Do Not change anything Else!
6) Boot into Ubuntu. Open up a Terminal Window. Follow the next instructions exactly, they will save you lots of trouble:
--1) Type "sudo passwd root"
---enter your desired root password twice
--2) type "su"
---enter your root password. you are now root.
--3) Type "sudo gedit /boot/grub/menu.lst
---this opens the grub boot menu file. do not alter this any more than you have to. if you screw this up, you will have to start over.
--4) Under the Windows XP selection at the very bottom of the file, you will need to add the OS X option.
---it will look like this:
title Apple OS X
root (hd0,0)
savedefault
makeactive
chainloader +1

that is exactly how it should look. following with the directions of OS X being on the first partition of the disk, it will be (hd0,0). if you do not have "chainloader +1" then it will not be selectable or boot.
--5) save menu.lst by clicking the save button, and closing the window. you can now exit terminal.
---lastly, restart your computer, and find that OS X is now selectable on the Grub Boot Menu.

this is as easy as it gets, and worked for me. if you have trouble or questions, feel free to PM me. i did this on a Mac Pro, so it should work for you the same way. This is on a single drive, not more than one for the OSes.

---

### Post by ZERO_SHIFT on 2007-11-25
Parallels and VMware are still good options:lolflag:

---

### Post by macaholic on 2007-11-25
> **bonestonne said:**
> don't be an ***. people post here for help, not people like you.

Boot Camp is the easiest way to triple boot on a Macbook. if you're really up for a challenge, you'll have to base everything in the Grub Boot Loader, and you'll need one hell of a partition table on that drive of yours. I condensed everything, and could probably get away with a 120gb drive doing it, but it would be very sketchy. you'll want at least 250gb to give each OS adequate space for data. XP can't have less than 5gb, Ubuntu cannot have less than 7 i think, for room to install packages and for updates. OS X needs 5.3GB, but you'll need room for updates. Linux also needs a Swap partition. if you have an 80gb drive, you're scraping the boundaries of what's possible.

1) get a copy of G-Parted Live CD
2) Install OS X on partition #1 just use the Disk Manager on the install CD to format the drive.
3) Boot from the G-Parted Live CD. Make the size partition you want for XP, but remember its size, thats most important
4) Install XP. When you do this, install to the exact partition you want. Don't delete or format any other partitions.
5) Install Ubuntu. install Ubuntu to the remaining partition created with G-Parted Live CD. Make sure that you have enough room, and extra for the Swap Partition. This will set up the Grub Boot Loader with Windows XP and Ubuntu on it. Do Not change anything Else!
6) Boot into Ubuntu. Open up a Terminal Window. Follow the next instructions exactly, they will save you lots of trouble:
--1) Type "sudo passwd root"
---enter your desired root password twice
--2) type "su"
---enter your root password. you are now root.
--3) Type "sudo gedit /boot/grub/menu.lst
---this opens the grub boot menu file. do not alter this any more than you have to. if you screw this up, you will have to start over.
--4) Under the Windows XP selection at the very bottom of the file, you will need to add the OS X option.
---it will look like this:
title Apple OS X
root (hd0,0)
savedefault
makeactive
chainloader +1

that is exactly how it should look. following with the directions of OS X being on the first partition of the disk, it will be (hd0,0). if you do not have "chainloader +1" then it will not be selectable or boot.
--5) save menu.lst by clicking the save button, and closing the window. you can now exit terminal.
---lastly, restart your computer, and find that OS X is now selectable on the Grub Boot Menu.

this is as easy as it gets, and worked for me. if you have trouble or questions, feel free to PM me. i did this on a Mac Pro, so it should work for you the same way. This is on a single drive, not more than one for the OSes.
I don't think bootcamp is the easiest way to go. rEFIt is definately a better option IMO. I agree w/ omax, that that guide is easy if you just make some minor tweaks to it (hard drive size, distribution etc.)

---

