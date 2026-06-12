---
title: "Windows XP  &amp; Boot-Repair will it work for me?"
date: 2012-08-19
forum: Any Other OS
---

### Post by peeyushj on 2012-08-19
I have read with interest  the discussion in this thread ; but not knowing much abt the technicalities am unable to decide abt the solution to my problem

I have a netbook on which I loaded windows XP folllowed by Ubuntu ( after upgrades it is now 10.10).  
The dual boot worked fine for few months , then the system started getting slow. Did a chkdisk /f on the windows partition and it started again showing some bad sectors. 
Again no problem for few days. Then windows started misbehaving. Was able to load windows after booting many times.
Now am unable to boot into windows. It shows only a blank screen. Am able to boot into linux but need to chkdisk and fix errors repeatedly.

Opened menu.1st in the grub. looks ok. apparently no problem with boot.ini but unable to load windows.

what should I do? Pl help

---

### Post by oldfred on 2012-08-19
Moved to own thread in Other OS since mostly a Windows issue.

Was in Boot repair thread:
[http://ubuntuforums.org/showthread.php?t=1831869](http://ubuntuforums.org/showthread.php?t=1831869)

Boot repair is primarily for Linux boot issues. It can only fix issues from grub booting into Windows and some minor Windows issues, but most Windows issues like chkdsk have to be done from a Windows install disk or RepairCD.

Also your 10.10 is now obsolete and unsupported. 10.04 was a long term support version and the new 12.04 LTS is long term support version.

From Ubuntu's Disk Utility, click on drive and check smart status. It can run a lot of checks but all I really know is green is good and anything else is major drive issues.

In Windows is it a virus or chkdsk repairs it?

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

If you run the fixMBR, it will reinstall the Windows boot loader and you need a Linux liveCD to repair the grub boot loader. If you have menu.lst you still have grub legacy not the current grub2. Grub2 became the standard with 9.10, but upgrades from older versions may still have had grub legacy (0.97)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by darkapec on 2012-08-19
If you have legitimate bad sectors, you may want to consider buying a new hard drive. Utilities like HDD regenerator are able to fix sectors a lot of the time, but this is only temporary. It is a means to boot up hopefully one last time and get any data you have backed up. 

With laptops / netbooks failing drives is very common. With all the movement etc, maybe consider upgrading to a SSD? An SSD will give you faster bootup times, faster shutdown times, faster transfer speeds and they are much more reliable.

---

### Post by codingman on 2012-08-19
I suggest you do a clean install of both, windows happens to create bad sectors all over the place because it doesn't seriously and officially support Ubuntu as a dual-boot, using wubi usually makes this occur, that's why I don't recommend wubi. I've never tried Ubuntu -- XP dual boot, only Ubuntu -- W7 dual boot. Have you had bad sectors when not having dual-boot? Ubuntu or Windows? If you would please give more information, we (the forums) may be able to help you better.

---

### Post by codingman on 2012-08-19
> **darkapec said:**
> If you have legitimate bad sectors, you may want to consider buying a new hard drive. Utilities like HDD regenerator are able to fix sectors a lot of the time, but this is only temporary. It is a means to boot up hopefully one last time and get any data you have backed up. 

With laptops / netbooks failing drives is very common. With all the movement etc, maybe consider upgrading to a SSD? An SSD will give you faster bootup times, faster shutdown times, faster transfer speeds and they are much more reliable.

Or this...

---

### Post by sakamoto on 2012-08-20
SSS indeed ):P

---

### Post by peeyushj on 2012-08-20
@ oldfred. I posted it on boot repair thread thinking that the problem may be solved by using boot-repair package by yannubuntu. I am not able to boot into windows and get a blank screen when i try to do so. In such a case I dont think that windows chkdsk wld be of much use. Would it be wise to run boot repair package in such a case?  I dont knpw if i can detect bad sectors through ubuntu?

Regarding 10.10 ver which Iam using for all my work; I am comfortable with it and am using gnome ver on my 3 yr old atom based netbook. On various forums  I have read that upgradng to 11.04 and subsequently to 12.04 may be problematic.  I am also not sure whether my netbook wld support unity. I use windows only sparingly for softwares such as SPSS which i am unable to install on wine. 

Thank you all for ur suggestions. I'll follow the steps as has been suggested by oldfred & then come back 2 u all for further clarifications.

---

### Post by oldfred on 2012-08-20
You can only run chkdsk from Windows. And some of the other repairs are from Widows repair disks.

Boot-Repair will fix grub2 and make some minor fixes, but cannot run chkdsk nor scan NTFS partitions for errors.

---

### Post by peeyushj on 2012-08-22
Regarding 10.10 ver which Iam using for all my work; I am comfortable  with it and am using gnome ver on my 3 yr old atom based netbook. On  various forums  I have read that upgradng to 11.04 and subsequently to  12.04 may be problematic.  I am also not sure whether my netbook wld  support unity. I use windows only sparingly for softwares such as SPSS  which i am unable to install on wine. As i said earlier I am not able to boot into windows.

In such a scenario pl tell

a) How can I distinguish between oldgrub legacy and grub2 ?. i dont know which one i have got installed. Is grub2 definitely better or can i leave the legacy in place?

b) should I upgrade from 10.10

c) should I run boot-repair package of yannubuntu?

Thnks in advance

---

### Post by oldfred on 2012-08-22
If you have menu.lst that is from grub legacy (0.97). If you have grub.cfg that is from grub2 which just became grub2 a few weeks ago and will be at version 2 in 12.10. It versions in Ubuntu were from 1.97 thru 1.99.

I went from 10.10 to 12.04 but installed fall-back so I still have the old menus not the new Unity.

gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

If performance may be an issue you can try Lubuntu or Xubuntu which use lighter weight applications. But you should upgrade to a supported version. Just download liveCDs and see what you like.

You can run boot repair, but it will not fix most Windows issues.

---

