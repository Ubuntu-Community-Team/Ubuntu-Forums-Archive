---
title: "Uninstall ubuntu , install xp"
date: 2011-07-13
forum: Any Other OS
---

### Post by YellowBronco on 2011-07-13
I'm trying to install windows XP over a ubuntu install, the computer specs are in my profile, but basically it is a amd 64x2 athelon, Ive got a 250g wd hd in it now, fully formatted, from external source, i.e. i put it in a external case and formatted it like a usb or floppy, ill name it ( x )l, then 2 other drive physically in the computer but un plugged with a bad install of umbuntu still on them, I've tried to take another computer and load the xp sys, program files, nvidia, and any other files i thought i might need in it, from another xp computer onto (x) hd. then tried to install xp from a valid xp disk, remember only ( x ) hd is plugged it,
now is the point( 5 days later) that i found this forum, and read @cstrikehero777 s [http://forums.techguy.org/linux-unix/836985-solved-anyone-know-how-remove.html](http://forums.techguy.org/linux-unix/836985-solved-anyone-know-how-remove.html)
problem report from sept 08, w/ almost 1000 views, alot of info in it, all of which i have tried, them it ends with "i solved the problem " and not how it was solved,

ok, back to xp, installation, i have a formatted 250 g hd installed, w/ xp disk in and running , in setup, windows tells me no hard drive is installed(weird that linux reads 6g ram?) i enter install xp professional setup anyway and come up with a -
"setupdd.sys
PAGE_FAULT_IN_NONPAGED_AREA"
MAKE SURE HARDWARE IS INSTALLED CORRECTLY YADA YADA YADA,,,, DISABLE BIOS??? HU? RESTART, F8 ,, ADVANCED STARTUP, YADA YADA YADA,,,, SELECT SAFE MODE,,,, YADA (i cant get to safe mode)
Technical information:
*** STOP: 0x00000050 (0xe26d7957, 0x000000000, 0xf418cad, 0x0000000002)
*** setup.sys - address F7418cad base at F73ec000. DateStamp 41107c8f

at this point i am thinking of making a backup of another working xp sys, (i have 5 of the same computer) and re-install off of that then put the right CD keys in Microsoft, but with the way  I'm going in circles there has to be a better way,
any help would be appreciated, thank u for yer time, Dan

---

### Post by mastablasta on 2011-07-13
Thi seesm to be a windows issue. if your hard disk is formated to ntfs or even if it's not formatted yet windows instal should recognise it. try running fdisk to see if there is any disk.
 
you might also have a hardware malfunction.

---

### Post by philinux on 2011-07-13
Moved to Other OS talk.

---

### Post by YellowBronco on 2011-07-13
its not the xp, its something to do with ubuntu locking me out, i cannot access the system to re-install windows and then re-install ubuntu, that is the end result desired, i had a failed install on ububtu, and i did it on 2 computers at the same time, full ububtu installs, both running vista origianaly, 
now i try to boot and the only thing i get on both of them is a failed ubuntu install , on my 2 most advanced systems, , they will not accept any, xp, vista, avg, system recovery, backups,msdos boot syschk or re-install of either 64 or 32 bit ubuntu on usb or cd, even with seting up bios in the right boot order,
to tell u this is the 5th system i have made unusable in as many days 
?????

---

### Post by jeffathehutt on 2011-07-13
Did you unplug both the data and power cable of the two "unplugged" drives in your system?  Also, are these drives PATA or SATA?  This sounds like a hardware issue to me.

---

### Post by Bart_D on 2011-07-13
> **YellowBronco said:**
> I'm trying to install windows XP over a ubuntu install, the computer specs are in my profile, but basically it is a amd 64x2 athelon, Ive got a 250g wd hd in it now, fully formatted, from external source, i.e. i put it in a external case and formatted it like a usb or floppy...

When setting up XP, I use the XP CD and delete ALL partitions from the HDD*. Then I create a partition for XP. Next I format it to NTFS (full format, not quick). Then the usual XP installation automatically starts....after the format is complete, that is. This has worked for me every time.

This has worked for me everytime. I have never formatted a HDD using an external source, as you described.....although it might be possible to do it.

* if you can't do this for some reason or the other, then STOP HERE. I don't care about lost data since I back up that data (only) before inserting the XP installation CD.

---

### Post by Bart_D on 2011-07-13
@OP: Is your XP disc a recovery disc? Or is it the kind of media that has a service tag associated with it?

Or is it a full Windows XP installation media.

---

### Post by YellowBronco on 2011-07-13
> **jeffathehutt said:**
> Did you unplug both the data and power cable of the two "unplugged" drives in your system?  Also, are these drives PATA or SATA?  This sounds like a hardware issue to me.
yes they are unpluged, 
hardware issue , on 2 very good machines, running extreemly well before, and its not the install software, i dont think, i got it strait from the ubuntu main site, but still i have the same issue with 2 seperate machines, ???

i got a software disk running ver. 6.06 from the library, if i ran that in the 11.04 would it have caused this problem?
i dont remember if i did, at first i didnt know there was a dif. ver. ???

---

### Post by YellowBronco on 2011-07-13
> **Bart_D said:**
> @OP: Is your XP disc a recovery disc? Or is it the kind of media that has a service tag associated with it?

Or is it a full Windows XP installation media.

disk and associated material say
microsoft windows xp professional ver. 2002 w/ product key
it not the service tag ones, i have them also, not a recovery disk , but those dont work either
its the real deal

---

### Post by oldfred on 2011-07-13
As Bart_D has already said. 

You have to have free unallocated space and a primary partition or a primary (sda1 thru sda4) NTFS formated partition with the boot flag for windows to find it and install. Use gparted to create a NTFS primary and add a boot flag.

---

### Post by YellowBronco on 2011-07-13
> **oldfred said:**
> As Bart_D has already said. 

You have to have free unallocated space and a primary partition or a primary (sda1 thru sda4) NTFS formated partition with the boot flag for windows to find it and install. Use gparted to create a NTFS primary and add a boot flag.

how do i do that?

---

### Post by oldfred on 2011-07-13
Not sure that this shows specifics of a NTFS partition but it is a choice for formating any partition.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by YellowBronco on 2011-07-13
> **oldfred said:**
> Not sure that this shows specifics of a NTFS partition but it is a choice for formating any partition.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

alot of great rtfm , i didnt get anything about ssd s though, anyone have more info on how to place them?

---

### Post by YellowBronco on 2011-07-13
alright after hours of reading another dead end, gparted can only work when u are in the ubuntu systen from what i read, and i cant get into it

---

### Post by oldfred on 2011-07-13
This is an Ubuntu forum. We help with dual booting but are not the experts on windows repairs.

Win7 forum
[http://www.sevenforums.com/](http://www.sevenforums.com/)

Mostly Linux but some general SSD info. You cannot use the better gpt partitioning for SSDs with windows unless you are booting with UEFI.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

---

### Post by YellowBronco on 2011-07-13
btw, im tracing the issue to either a ide controler erased, a boot.ini not installed on the hadrdrive , sata function taken away by having no information to run it, missing an msi controler, amd64x2 compatibility issues, Bus Master IDE Controller missing, ssd incompatibility w/ ubuntu, Incorrect Ntbootdd.sys driver, im still at it though
[B]
[/B]

---

### Post by YellowBronco on 2011-07-14
now im getting a mp-bios bug: 8254 timer not connected to IO-APIC
then KERNEL panic- not syncing: IO-APIC + timer doesnt work
debug and send report
then try booting with the 'noapic' option

????im so lost

---

### Post by mastablasta on 2011-07-14
> **YellowBronco said:**
> alright after hours of reading another dead end, gparted can only work when u are in the ubuntu systen from what i read, and i cant get into it
 
 
gparted works in ubuntu if you boot live disk. In fact to do any changes to the drive you need to boot into live session.
 
gparted also has it's own disk: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by YellowBronco on 2011-07-22
well, its been almost 2 wks and im finaly to where i can reinstall   11.04, it was my own stupidity, i put a version 6 on top of 11.04. i   thought it was just info from the library , not a whole new install.   like i said^ i like ubuntu, ive been too enamored in the bill gates   world to fully get it all of ubuntu yet, i guess if u are starting out   fresh with it it is easier then having to relearn things 
alot of my problem is i think i know how it works, well it only works that way in windows,, lol
there is probably alot of ways to do this but i nuked the disks all hds ,   re-installed a new os , xp not the vista stuff, had to re-find all   drivers this way and reinstall from bios, in order to do that i had to   take the motherboard out and find the codes on the back side of it
please dont anyone else do what i did
dan

---

