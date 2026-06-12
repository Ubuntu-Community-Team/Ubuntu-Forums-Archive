---
title: "What partitions do I create when multi-booting?"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by claw_atticas on 2007-12-21
I currently have Ubuntu 7.10, and XP running, but I want to repartition the space I have to try different Linux distros (I've heard nothing but good about Mint, and I've heard good things about SUSE), and my question is

Could, instead of '/' as the root directory, I use '/ubuntu/'? Maybe for different distros, I could have /mint/ be the root for Mint Linux, /kubuntu/ for Kubuntu, etc, etc...

In other words, how to I make multiple root directories, one for each distro?

---

### Post by thelatinist on 2007-12-21
> **claw_atticas said:**
> I currently have Ubuntu 7.10, and XP running, but I want to repartition the space I have to try different Linux distros (I've heard nothing but good about Mint, and I've heard good things about SUSE), and my question is

Could, instead of '/' as the root directory, I use '/ubuntu/'? Maybe for different distros, I could have /mint/ be the root for Mint Linux, /kubuntu/ for Kubuntu, etc, etc...

In other words, how to I make multiple root directories, one for each distro?

You just install these other distros.  Each installer should recognize your previous installations and add them to your menu.lst so that you will have the correct options in your GRUB boot menu.

Each of these installations will be on separate partitions.   In whatever distro you are booting into, its own partition will always be /.  You can then mount the other partitions however you want by creating a mount point in /media and then mounting to it.  If you are in kubuntu, for example, you can mount your ubuntu partition at /media/ubuntu.  Your Kubuntu partition will be /.  If you then reboot into Ubuntu, your ubuntu partition will become / and you can mount your kubuntu partition in /media/kubuntu.

---

### Post by coffeecat on 2007-12-21
Probably the best way is to use Gparted on the live CD to resize your current partitions and create new ones. A few points to think about:

You are limited to four primary and/or extended partitions per hard drive. An extended partition is used as a 'container' for logical partitions. Linux can boot from a logical partition but Windows must be in a primary partition. Primary/extended partitions are numbered sda1 - 2 - 3 -4. Logical ones are numbered sda5 and upwards. (Limit of 15 with the newer libata kernel drivers.) So - best way is to leave Windows on a primary partition (usually sda1) and put your Linux installs on their own logical partitions.

You only need one swap partition which can be shared between the different distros. The only exception to this is if you are going to rely on suspend to swap.

If you want you can have a shared /home partition, but you may come across permission problems where different distros set up users with different UIDs. Search the forum for pros and cons of this. Or you could have a shared data partition. VFAT - no problem with permissions but the disadvantages of FAT32. Ext3 - possible problem with permissions if the UIDs are different.

GRUB - Some distros (for example Ubuntu) are good at detecting other distros and setting up a multi-booting grub. Others (eg Fedora :( ) are hopeless at this.

---

### Post by Duck2006 on 2007-12-21
If you are using one home partition for all your distros that you are running, make sure you have a different user name for each distro. As "coffeecat" posted you may have permission problems, By doing it this way you will decrease the space you need for each distro you are running.

---

### Post by claw_atticas on 2007-12-21
Thanks a lot for the help. Also, is there a way I can edit the GRUB to have a certain distro as the default? (Such as automatically start up XP or Ubuntu if nothing's pressed for so many seconds) And also is there a way to change the amount of time until a key is pressed? (I don't like only having 10 seconds. 30 seconds is much better)

---

### Post by Duck2006 on 2007-12-21
Yes, in your menu.lst look for the line that has 

default         0

change the 0 for what every entry it is that you want to boot first.

---

