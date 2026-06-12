---
title: "Grub detection of Windows"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by carrajung on 2007-04-25
I have just installed Ubuntu 6.1 and Grub has not added Windows XP to the options.
This is a real problem because I can no longer boot into Windows.
Can anyone tell me what has gone wrong????
All other Linux distros have gone OK.

---

### Post by gj15987 on 2007-04-25
You'll have to edit /boot/grub/menu.lst. Don't quote me on this but i'm pretty sure you'll need something like # ```
# For booting Windows NT or Windows95
title Windows NT / Windows 95 boot menu
root        (hd0,0)
makeactive
chainloader +1
```

Don't try it until someone else confirms though :(

---

### Post by carrajung on 2007-04-26
That sounds great but I would like to know why this is happening in the first place.
I cant beleive that the Ubuntu team could miss something this basic.

---

### Post by carrajung on 2007-04-26
Can anyone help me on this?

---

### Post by heartbeat on 2007-05-17
I've got the same problem.

Win XP is no longer in my GRUB menu

---

### Post by Terl on 2007-05-17
You are right, normally windows is picked up during installation and added to Grub's menu.  There are times when it may not happen.  What is your drive setup for your pc?

When you are in Ubuntu could you run the following and post the results?  (the last part is -small L)

```
sudo fdisk -l
```

---

### Post by heartbeat on 2007-05-17
Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32300   244187968+   7  HPFS/NTFS

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4379    35174286   83  Linux
/dev/hdc2            4380        4865     3903795   82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10010    80405293+   c  W95 FAT32 (LBA)


This is my output for fdisk -l

the upper disc (250gb) is the drive with winxp

i know i have to add something in the menu.lst but i've added windows to it.
title		Windows XP
root		(hd1,0)
makeactive
chainloader	+1

but when i try to boot windows it wont boot. It says Starting up and nothing happens.
when i change root to (hd0,0) i get an error (error 13)

---

### Post by Terl on 2007-05-17
Do you have a mix of drives; like one sata and the other ide?  I know this has caused issues with other folks too.  There are other posts in this forum.  I will have to look further.  I am not sure how to go from here.

---

### Post by heartbeat on 2007-05-17
Windows is on a SATA drive and Ubuntu is on an IDE drive

---

### Post by gn2 on 2007-05-17
Have you tried the Gag bootloader?

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

Or read through this:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by heartbeat on 2007-05-17
when i install gag, do i need to remove grub?

---

### Post by Terl on 2007-05-17
If grub is on your MBR now installing gag will wipeout (over write) grub for you

---

### Post by gn2 on 2007-05-17
Here are comprehensive instructions for Gag from Herman's excellent website: [http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

---

### Post by heartbeat on 2007-05-17
and how do i install Gag? i'm still a noob with ubuntu

---

### Post by Terl on 2007-05-17
> **heartbeat said:**
> and how do i install Gag? i'm still a noob with ubuntu

See the link in gn2's post above.  It explains everything.  Very, very easy to do.

---

### Post by gn2 on 2007-05-17
> **heartbeat said:**
> and how do i install Gag? 

Scroll down to the section under the heading "Unpacking Gag in Ubuntu"
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

---

