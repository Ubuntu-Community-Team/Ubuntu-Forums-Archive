---
title: "Catastrophe - Grub won't start at all"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by kyokan on 2007-03-21
Hi guys, I'm totally new to Linux and this is scaring me:

I downloaded the 6.06 release and burned it to cd, and it'll boot to the cd just fine, had a play around and decided to install. I have 5 hard disks in my system, two on normal IDE, two on an on-board IDE RAID controller and one one on an on-board SATA controller. The only two disks I'm concerned about are the normal IDE disks.

The primary master contains a Windows XP installation and a Windows Vista installation, and I would like to install Ubuntu onto the primary slave. Simple enough...

When I boot from the CD I get the Ubuntu main menu, and I select the first option, and then I get a message on my monitor saying "frequency out of range - 81hz" or something similar, but when it's finished loading I can see my desktop fine. 

I go through the installation procedure and install to hdb and everything appears to be fine, it says "Please restart your computer to complete".

However, when I reboot all I see is this:
"Loading Grub, please wait...
 Grub Stage 1.5
 Error 17"

And that's it. I don't mind the fact that Ubuntu isn't working yet - I can wait to get that fixed but I can't boot into Windows anymore! Alarm! Alarm!

Any help you guys can offer would be greatly appreciated. By the way, I've tried re-installing Ubuntu and it just does the exact same again...

- Richard -

---

### Post by mac.ryan on 2007-03-21
I am far from being either a linux- or a grub- guru, however, what I understand is that error 17 indicates GRUB can't understand what type of partition you are trying to use. From

[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

I read: "Error 17 : Cannot mount selected partition - This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

So, a relevant info to be posted in the thread would perhaps be the output of:
```
sudo fdisk -l
```The content of your  "menu.lst" file might also be useful

---

### Post by kyokan on 2007-03-21
Thanks for the reply, but unfortunately my pc uses wireless networking to connect to the internet, which doesn't work in Ubuntu Live, so I can't copy and paste onto the forum.
 
In essence, sudo fdisk -l gives for hdb
 
Device Boot Start End Blocks ID System
/dev/hdb1 1 4553 36571941 83 Linux
/dev/hdb2 4554 4884 2658757+ 82 Linux swap / Solaris
/dev/hdb3 4885 9729 38917462+ 83 Linux
 
Where's menu.lst? I couldn't find it. Also I've discovered that if you open Computer from the places menu all my hard disks are listed but if you double click on any one of them it says:
" Unable to mount the selected volume.
error: device /dev/hda2 is not removable
error: could not execute pmount "
 
Thanks again,
- Richard -

---

### Post by confused57 on 2007-03-21
Try booting the live cd, open a terminal, enter:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdb1 /media/ubuntu
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/boot/grub/device.map
```

To summarize the above:
you make a directory /media/ubuntu
mount /dev/hdb1 to /media/ubuntu
display the contents of your menu.lst(short for menu.list)
show your device.map

Post the above & maybe we can figure out what's wrong.

Wouldn't hurt to check in your bios and post the boot order of your hard drives.

---

