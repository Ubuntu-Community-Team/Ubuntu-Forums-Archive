---
title: "Install Ubuntu without CD? Possible or not?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Edubuntu on 2007-05-23
Hello

First of all i am new to both Linux and Ubuntu so i have 0 xp regarding the issues of installing, running and configuring either of those two.

Second, i'd really like to have Ubuntu on my Laptop but my CD-DVD ROM isnt working so i cant use a CD to install Ubuntu. If i send my laptop to the shop where i bought they'll need 2-3 days to fix the problem but i cant afford to loose 2-3 days (i do alot of eLearning on my laptop while i am at work or school) because i have lots of exams at the uni right now.

So is there any guide on HowTo install Ubuntu without a CD?

I googled it and found a guide that's from 2005 and i doubt it will still work.
If there is any "easy" step by step guide please post it in here.


Thanks

---

### Post by Kobalt on 2007-05-23
You can [install Ubuntu from a USB stick]("https://help.ubuntu.com/community/Installation/FromUSBStick") if you've got one.

---

### Post by mikewhatever on 2007-05-23
I am not sure your have Windows, but no harm to mention [https://wiki.ubuntu.com/install.exe](https://wiki.ubuntu.com/install.exe)

---

### Post by Edubuntu on 2007-05-23
Thanks guys.
I will try those links you posted.

Like the english say "Cheers"

---

### Post by ed_agamemnon on 2007-05-23
there's a 'netinstall' option too - run a search...

---

### Post by Carlos Santiago on 2007-05-23
Yes, it is possible. ;-)

I also had my CD broke and I was able to install Ubuntu mounting the ISO image on boot.

It was a little tricky, but it is not hard:

1) Install grub for windows ([https://sourceforge.net/projects/grub4dos](https://sourceforge.net/projects/grub4dos))

2) Configure a grub option to use the initrd.gz and vmlinuz files that you find in [http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current/images/hd-media/)
NOTE 1: In fact I used the initrd.gz and vmlinuz files that I found in ttp://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/
because they were already installed. But you should try with the new ones. But if for some reason they do not work, you may try with the dapper ones. Those work fine for me!

3) Download the Alternate ISO and save it in the root of a partition. Don't use spaces on its name!
NOTE 2:I use my D: partition that is formated in FAT32, but it might work on NTFS partitions. I dont know!

4) Reboot and select that grub option

Now the tricky part:
5) When it is searching for your ISO it fails !!! Activate a console (I think it was with ctrl+alt+F1) and type:
mkdir -p /dev/loop
ln /dev/loop0 /dev/loop/0

6) Research for CD. 

7) Now it should work!

---

### Post by envmyz on 2007-05-23
For those who dont want to mess with the boot.ini try this..

Create an unpartioned space, thats all. One partition for Windoz and one black unformatted.

[http://downloads.sourceforge.net/ins](http://downloads.sourceforge.net/ins)... &big_mirror=0

Download instlux, run the application and choose to reboot later.

Download the initrd.gz and vmlinuz
[http://archive.ubuntu.com/ubuntu/dis...ages/hd-media/](http://archive.ubuntu.com/ubuntu/dis...ages/hd-media/)

After downloading (Put them on your desktop)
Rename vmlinuz to linux

Copy these two file to the c:\instluxNETUbuntu6_06 folder (overwrite them)

Copy the alt_feisty ISO to the root of C:\

Reboot computer, select Ubuntu, then again.

ALL DONE!!

Reboot into windows after finished and instlux will un-install itself and your all set!!

Hope this helps, Cheers

---

### Post by Carlos Santiago on 2007-05-24
Envmyz, your links are broken!

---

### Post by Simran on 2007-05-24
I managed to break my CD-Drive on my laptop so I found this guide to install from a USB key. Worked first time really well :)

[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/#more-64](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/#more-64)

Enjoy 

Simran

---

### Post by silent1643 on 2007-05-24
[http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

---

