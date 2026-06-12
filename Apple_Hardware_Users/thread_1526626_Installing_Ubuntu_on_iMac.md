---
title: "Installing Ubuntu on iMac"
date: 2010-07-08
forum: Apple Hardware Users
---

### Post by fipz on 2010-07-08
Hello everyone, 

I own a 8.1 iMac and i decided to dual boot my os x with ubuntu (or to be honest any working distro would fit me in case for some reason ubuntu wuoldn't work).

Now I know you might say "just google it its full of tutorials" but I'd like to NOT use rEFIt or such tools to do so, is it possible? 

If rEFIt is the only way to do so does anyone know in details what rEFIt does (documentation is very poor in my opinion) and could explain me?

thanks in advance.

EDIT: as i said if ubuntu is impossible to install in such way and you'd be so kind to give me some other names it'd be appreciated (possibly some spread distros like open suse, fedora or such) <--- if rules allow it, being ubuntuforums.org im not sure it would be liked lol

---

### Post by fipz on 2010-07-08
bump, really noone?

---

### Post by linux-hack on 2010-07-08
Yes it is possible to do that without rEFIt but the thing is that its much better to do sow. If you have a problem with ubuntu you still have full controle with the refit on the partition. I have a macbook pro 5,3 and have a dualboot with ubuntu and mac OS with refit and it's simply perfect. Just be careful when you install ubuntu to install the grub boot loader to the partition that ubuntu is and not the one with the OS X...

Did you read this : [https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

---

### Post by linux-hack on 2010-07-08
> **fipz said:**
> 

If rEFIt is the only way to do so does anyone know in details what rEFIt does (documentation is very poor in my opinion) and could explain me?


The thing is that macs don't have a BIOS .. So to clear that "problem :D" you use refit with simulates a BIOS on the computer so that linux will work better on boot and so on.

This is from the refit website :

> 
This section should probably be called “What is Boot Camp anyway?”. There is no final word on what is worthy of the label “Boot Camp” and what is not. Personally, I prefer to use more precise terms like “BIOS emulation”, “hybrid GPT/MBR”, “BIOS-based booting” or “legacy OS booting”.

Here are some facts about Boot Camp to get a picture of what is involved in making it work. See the following sections on what is actually needed/recommended for booting Windows or Linux.

When Apple released the first Boot Camp Beta in April 2006, they actually released three separate pieces that were all required to make it work:

The Mac OS X 10.4.6 Update added several capabilities to the OS and its tools:
Online resizing of HFS+ volumes (kernel and diskutil)
Hybrid GPT/MBR partition table support (diskutil and Disk Utility)
Ability to select Windows partitions and CDs as boot volumes (Startup Disk and bless)
Firmware updates for the iMac, Mac mini and MacBook Pro added a BIOS compatibility module, including detection of BIOS-bootable disks and CDs in the built-in boot volume chooser. This has been part of Intel Mac firmwares ever since.
The actual “Boot Camp” download containing the “Boot Camp Assistant”. The Boot Camp Assistant has exactly two functions. It provides a nice user interface to resize the Mac OS X partition and create/remove a Windows partition, and it contains a CD image with Windows XP drivers for Intel Mac hardware (including a Startup Disk control panel for Windows).
Summary: You don’t need the actual Boot Camp package to install Windows or Linux, but it usually helps.

More in here [http://refit.sourceforge.net/myths/](http://refit.sourceforge.net/myths/)

---

### Post by fipz on 2010-07-08
mmm any hint on how to do without rEFIt? 

I'm pretty sure I'll fall in love with it once my ubuntu will be installed without (thats my modus operandi lol first i do clean then i add tools) but i'd like without first.

I remember i had troubles installing grub

my partition tables was like

sda 1  EFI partition (misterious empty partition lol)
sda 2 hfs (os x <3)
sda 3 ext4 (ubuntu)
sda 4 would have been swap but i forgot to add lol

it just wouldn't install grub in sda 3 , it would say "error i cant do this" but at my question "do you need help mate?" i had no answer.

what did i do wrong if you know?

PS: thanks for the explanation, i knew that imacs have EFI (why i'm quitting pcs) but really didn't find that page on sourceforge lol. (myths and facts)

---

### Post by linuxopjemac on 2010-07-09
Here some reports of people installing Ubuntu without rEFIt.
[http://mac.linux.be/content/installation-karmic-koala-macbookpro-12-without-refit-chainloading-xp-0](http://mac.linux.be/content/installation-karmic-koala-macbookpro-12-without-refit-chainloading-xp-0)
[http://mac.linux.be/content/single-boot-linux-without-delay](http://mac.linux.be/content/single-boot-linux-without-delay)
[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=60](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=60)

---

### Post by fipz on 2010-07-09
well first of all thank you for your reply, second, the links you given me talk about triboot or anyboot with rEFIt, can't i do a dual boot without all that hassle? like i do on pc boot the cd install and tada ubuntu? also because pressing alt on startup should be an advantage i dont mind it (tho first time it didnt even show a linux partition)

---

