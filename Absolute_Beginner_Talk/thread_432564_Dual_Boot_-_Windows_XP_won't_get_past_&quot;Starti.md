---
title: "Dual Boot - Windows XP won't get past &quot;Starting Up ...&quot;"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by tom.clements on 2007-05-04
Continuing on from my previous post ([http://ubuntuforums.org/showthread.php?t=423938]("http://ubuntuforums.org/showthread.php?t=423938")), I am still unable to get Windows XP to boot from Grub. It just hangs at "Starting Up ..." (which I believe is a grub message) - so does this indicate its not chainloading properly? I can restore the mbr using fixmbr and windows will then boot fine, but obviously then I don't have access to Ubuntu unless I use a boot cd.

I have three SATA drives and Windows is installed on sda1, sdb1 is an NTFS formatted scratch disk and Ubuntu 7.04 is installed on sdc1. Having suspected that sda1 was somehow corrupted by a previous resizing process I backed up my data and deleted all partitions from all drives and started again. At about 2am this morning I finally got Ubuntu installed and rebooted to grub (installed on hd0 - which I believe translates as expected to the mbr of sda) and selected Windows and guess what - "Starting Up ..."!!! DOH! Ubuntu boots fine.

This i really is getting annoying.. i've been stuck for 2 - 3 weeks now.. I really want to have Ubuntu, and have even tried installing 6.06 LTS and 6.10 with the same results. On my previous machine (whose primary disk was IDE) - it worked straight from install with a rezised partiion and ubuntu in the remaining space.

I have posted my device.map, menu.lst, and fdisk -lu output for information, but to my mind I can see nothing wrong!! 

menu.lst:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=01f26b83-b842-4d2c-880e-718ccf76a006 ro quiet splash noapic
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=01f26b83-b842-4d2c-880e-718ccf76a006 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

device.map:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

fdisk -lu output:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    80405324    40202631    7  HPFS/NTFS

Disk /dev/sdc: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    77031674    38515806   83  Linux
/dev/sdc2        77031675    80405324     1686825    5  Extended
/dev/sdc5        77031738    80405324     1686793+  82  Linux swap / Solaris

Any advice gratefully recieved, even if it means putting my IDE drive back in and using this as the main boot / Ubuntu drive. Having searched on google et al, this doesn't seem to be a common problem, but few if any fixes seem to have been found! 

Cheers,

Tom.

---

### Post by louieb on 2007-05-04
I saw a solution to this in another post it made no sense that it would work but I'll pass it on anyway.
According to this guys device.map and fdisk windows the root statement should have been **(hd0,0)**   but he changed it to **(hd1,0)** and it worked. 

Go figure? Maybe there is something strange going on with GRUB and device mapping.

---

### Post by macogw on 2007-05-04
Try what louieb said.  My mom's computer has the hd0 and hd1 backwards in menu.lst as of in device.map, and it works.  If I make the menu.lst say what the device.map tells me it should say (and what kernel updates make it say), I can't boot.  I locked the kernel version so that it doesn't update and leave her locked out of the computer with me 250 miles away.

---

### Post by tom.clements on 2007-05-04
thanks louieb and macogw I'll give it a go and post back..

---

### Post by tom.clements on 2007-05-07
I tried changing from (hd0,0) to (hd1,0) and no luck... any more bright ideas anyone?!

---

### Post by watterman on 2007-05-07
I believe I have the same problem as tom.clements, but only since upgrading ubuntu 6.10 to 7.04.

I have WinXP on first partition of sda. Ubuntu is also on this drive in sdb. Grub is on hda.

If I unplug the IDE drive (hda) then WinXP will boot no problems at all.

With the IDE drive plugged in, selecting WindowsXP from the grub menu will fail to load it.
Initially was getting the endless "Starting up...". By removing the map commands from menu.lst I would get "NTLDR Missing".

Windows section of menu.lst

title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
map (hd1, hd0)
map (hd0, hd1)
chainloader +1


device.map:

hd0  hda
hd1  sda


I have also tried:
rootnoverify
fixboot in windows recovery console
hd0 in place of hd1 in above code snippet

All these things haven't worked. Any ideas?

regards,
Adrian.

---

### Post by Ric95 on 2007-05-07
I had such a problem when I first installed dual boot. The odds are slim, but boot with any partitioning tool and check to see if the Windoze partition properties got set to 'hidden'.

---

### Post by tom.clements on 2007-05-08
Unfortunately the partition is not set to be hidden.. the 'boot' flag is checked however..

---

### Post by Terl on 2007-05-08
This is indeed odd.  When is the last time windows was booted?  Could there be something wrong with its install?  Did anything change with hardware since windows was last booted?  Maybe this is a windows issue...

---

### Post by tom.clements on 2007-05-08
the last time windows booted successfully was before I installed grub! It was a fresh install, having previously deleted the windows partition and starting completely from scratch, although the behaviour is exactly the same as before reinstalled windows.

I guess I need to work out what grub is / or should be dong at the point at which it gives the "Starting up.." message. Could there be an issue with boot.ini?

---

### Post by jmore9 on 2007-05-08
I don't know if this will help but when i dual boot with XP i install xp first on the 1st hard drive. Then i install what ever version of linux on the second hard drive.  I use grub just as it is installed during the install.  I had one time with something like the problem you have , but it was because i used partion magic to format the hard drives and XP (pro) did not like that so i used the formatter with xp and everything was just fine.  Myabe this will help you in some way maybe not

---

### Post by tom.clements on 2007-05-08
thank you for the suggestion.. but this is what I tried when I reinstalled windows and ubuntu. Windows setup configured the partition and formatted it, prior to installing windows and then Ubuntu did the same for its install, before installing grub to the first drive.

---

### Post by Terl on 2007-05-08
Has the drive configuration changed at all?  I ask because of this statement in the first post:

> ...even if it means putting my IDE drive back..... 

It made me think windows is confused (easy to do :)  )  It may be irrelevant as you said you just did a complete reinstall.  Is your BIOS ok?

I have a sata setup too, just two drives.  I have xp on sda and ubuntu feisty on sdb.  Ubuntu has always placed Grub on sda and I have never had a problem.  I have done it with multiple pc's too.  This is why I find it odd.  

If you have the utilities installed on ubuntu you could access your xp partition and read/check the boot.ini file and see if there is something amiss.  You could try starting with your xp cd and using it to boot windows...maybe see if it has a problem.  I still think there may be something up with your windows install.

---

### Post by tom.clements on 2007-05-08
you have a sharp eye terl! but no, drive config hasn't changed.. that suggestion was a clutching at straws idea I had, that somehow because I was all sata it wasn't liking it. The three previous and successful dual boot installs I have performed were all using an ide drive as the first one. 

I will look at the boot.ini but not sure I would recognise a problem with it necessarily. The fact that the behaviour has remained following a complete reinstall (following partition deletion and recreation) worries me. What hasn't changed is the bios.. could there be anything there? I am running an AMD 3800+ 64 X2 on a ABIT K9NS m/b.

---

### Post by louieb on 2007-05-08
The one time I had to reinstall windows was just after shrinking the Windows partition. Did not even install Linux or GRUB then, just used the GParted live CD to shrink the partition. Did not think at the time to check the  boot.ini file.  

  Tried fixboot and fixmbr from the Windows recovery console neither worked. Wound up reinstalling XP in the smaller partition. Just wondering when you installed Ubuntu did you shrink the XP partition as a part of the install.

I've only got one hard drive (sata)  on that machine. Since you wonder about the boot.ini file heres  mine.
```

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 


```
Later I installed Ubuntu and GRUB on that machine and everything worked just fine.

---

### Post by Terl on 2007-05-08
If the drive setup has not changed I doubt there is anything amiss with BIOS.  

Hmm, have you tried using the windows cd and using recovery console to boot windows?  Just to make sure it boots....

I would definietly check the boot.ini file

---

### Post by tom.clements on 2007-05-08
the very first time I installed Ubuntu on this machine I did get ubuntu install to resize the windows partition to make space for ubuntu. In fact I did it wrong and make the windows one too small - and as it happens windows wouldn't boot (irrespective of grub) - got some terrible bios message about the drive size beign wrong or cannot find operating system (can't quite remember). Anyway from then, I used gparted to delete the ubuntu partition and resized windows back to what is was orriginally, ran fixmbr and fixboot and hey presto my windows was back again! phew. I then installed ubuntu to a 2nd drive, and put grub on the 1st and thats when the "Starting up.." problems began.. 

After that, I deleted all partitions and started again but still the problem persists - although I can always recover my windows install using fixmbr.

terl - when you say use the windows xp disc to get it to boot.. I've been playing with these kinds of things for years but never realised I could get the install disc to boot a partition (thought the best it could offer was intall or recovery console!).. how would I do this?

---

### Post by Terl on 2007-05-08
I may be confused (I am at work right now) but I thought one of the options on the setup was to safe boot the windows install.  I could be wrong (surely not unknown :) ).  

It could be worth trying to do a fixmbr and then a grub reinstall after we make sure windows is booting itself.

So, on the latest installs, I assume you wiped, reformatted and did clean installs of windows and ubuntu?  That is what it sounds like...just checking.  I know windows gets ticked off if its partitions are resized.

---

### Post by tom.clements on 2007-05-08
I can definately get windows to boot with a fixmbr, reinstalling grub screws it up.. and your quite right that the new installs were on deleted and recreated and formatted partitions. 

I'm not entirely sure what my next move might be.. am tempted to make the ubuntu drive the first one, windows the 2nd and then putting grub on the mbr of the ubuntu disc (which would now be the first) and then using map to try and boot windows.

---

### Post by drowner on 2007-05-08
I know nothing, im a real n00b.....

, but if this happened BEFORE grub was installed, and then you had to reinstall windows, and now its happening again, it DEFINITELY sounds like a win problem

---

### Post by tom.clements on 2007-05-08
negative unfortunately, wasn't happening before grub was installed.. windows worked just fine pre-grub!

---

### Post by Terl on 2007-05-08
Have you thought of trying the dual boot with the windows ntldr?  Check here for one example:  [Dual boot with ntldr]("http://www.aboutdebian.com/dualboot.htm").  It is about half way down the page.

I can't say why your setup is not working.  I will reread the posts and see if I can come up with something more.

---

### Post by tom.clements on 2007-05-08
many thanks for your help terl.. I did wonder if it was possible to use ntldr but I will check your link and give it a go. I don't really mind what boot manager I use, just so long as it actually works - it would be v nice to know why grub isn't playing ball though.

---

### Post by Terl on 2007-05-08
I do wonder about the BIOS now.  Bear in mind, I know precious little about RAID but I noticed this in your first thread:

> OK, posting has kind of been my last resort because I know there are quite a few threads and sites on how to configure grub.. but for the life of me I can't work out why I can't get XP to boot. I have a three HDD setup, all are SATA and I have reduced the complexity of the drive setup and partiioning down to what I think is the simplest I could make it (previously I had two drives on a Fake RAID - which I got rid of because I don't think I gained much, with Ubuntu and XP on the same drive).


It might be worth checking your BIOS to see what it thinks you have set.  Take this as a maybe as I don't know too much about RAID setup.

I never tried the NTLDR methods either but they seem viable.  There are lots of sites with info about it.  I just googled "ntldr linux dual boot".

I also wondered if there was some issue with the 64 bit and Feisty.  I noticed earlier on this thread Watterman posted with a similar problem.

---

### Post by tom.clements on 2007-05-08
I took raid out of the equation at the point of repartioning and reformating.. fake raid was't doing much for me anyway I don't think. BIOS on the face of it looks to be ok, boot order is as expected (i.e. windows drive set to be first in order)..

I will try the 64 bit version of feisty.. I wasn't going too on the basis that the 32 bit version should be entirely compatible with my chip, and I only sacrifice a small amount of performance for the benefit of improved application compatibility (i.e. flash etc not working in 64bit - although I am aware of work arounds).

---

### Post by mahiyar on 2007-05-08
There are many holes (by holes I mean gaps in understanding)  in the grub implementation in feisty, I had similar problems trying to set up IDE and SATA drive and trying to boot from IDE (see here [http://ubuntuforums.org/showthread.php?t=418604](http://ubuntuforums.org/showthread.php?t=418604)) finally I forgot about booting from IDE and booted from grub in SATA. For getting a good grip on grub try this site [http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot), here you will learn about CLI interface of grub, where you can feed in the exact lines of menu.lst and see the errors/results.

---

### Post by Terl on 2007-05-08
> **tom.clements said:**
> I took raid out of the equation at the point of repartioning and reformating.. fake raid was't doing much for me anyway I don't think. BIOS on the face of it looks to be ok, boot order is as expected (i.e. windows drive set to be first in order)..

I will try the 64 bit version of feisty.. I wasn't going too on the basis that the 32 bit version should be entirely compatible with my chip, and I only sacrifice a small amount of performance for the benefit of improved application compatibility (i.e. flash etc not working in 64bit - although I am aware of work arounds).

Oh no, I did not mean to try the 64 bit.  I assumed (bad thing, I know) you were already trying the 64.  I agree, stick with the 32bit. 

I would try the ntldr idea though.  Seems like a workaround.

---

### Post by tom.clements on 2007-05-09
I tried configuring ntldr using the util 'bootpart' and guess what.. when I choose linux is hangs! Almost exactly what grub does when trying to load Windows! AGH!

Am starting to think about doing an ubuntu install to external usb drive and just booting from it when I want to use linux..

---

### Post by Terl on 2007-05-09
IIRC, grub was in your mbr.  If you ran fixmbr and then set up the nt loader you should reinstall grub to the root partition of the ubuntu partition.  This should fix it.

---

### Post by tom.clements on 2007-05-09
many thanks for the suggestion.. but I should have mentioned that prior to trying ntldr I switched the hdds round so that the ubuntu drive was first and installed grub to it - the windows drive was second with a fixed mbr . I then configured grub to boot the windows drive using the map commands but it didn't work. 

At this point I then decided to go for the ntldr route - I switched the drived back round so windows was first confirmed it boot successully.. switching boot order got me a booting ubuntu so grub is installed ok and then switched it back to use bootpart.

I will reinstal grub just to be absolutely sure however!

---

### Post by Terl on 2007-05-09
You may need to double check the nt loader again after the drive switching.  Switching the drives will change their designations, I believe.

---

### Post by tom.clements on 2007-05-10
can I just confirm my understanding of using nldr.. Do I need a separate /boot partition to which grub should be installed? At the moment grub is installed to the mbr of the main ubuntu partition and it is here that I am pointing boot part.

---

### Post by tom.clements on 2007-05-10
.. so setting up a separate boot partition, installing grub to the mbr etc, and then using ntldr didn't work.. it just hangs when I select Ubuntu in ntldr! Am close to abadoning the project.. try as i might, short of using the bios to change boot drives each time this machine simply won't dual boot windows and ubuntu! Exceptionally annoying.. but am afraid my default postiion is xp as there is software I use (such as Adobe Audtion and Captivate) that I have struggled to get going with WINE.

---

### Post by Duck2006 on 2007-05-10
> /dev/sda1 * 63 488375999 244187968+ 7 HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 63 80405324 40202631 7 HPFS/NTFS

Disk /dev/sdc: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes

Device Boot Start End Blocks Id System
/dev/sdc1 * 63 77031674 38515806 83 Linux
/dev/sdc2 77031675 80405324 1686825 5 Extended
/dev/sdc5 77031738 80405324 1686793+ 82 Linux swap / Solaris

The problum is that grub is seeing three bootable devices on your system, so (hd0) (hd1) will not ghet you to boot windoze. Change your boot drive in your BOIS to boot the drive that has Linux on it and in your menu.lst add these lines to your windozes lines and see if it will work for you

map (hd0) (hd2)
map (hd2) (hd0)

---

### Post by brennydoogles on 2007-05-10
> **tom.clements said:**
> you have a sharp eye terl! but no, drive config hasn't changed.. that suggestion was a clutching at straws idea I had, that somehow because I was all sata it wasn't liking it. The three previous and successful dual boot installs I have performed were all using an ide drive as the first one. 


This seems to suggest to me that you are able to mix IDE and SATA drives... is that true?? I have never dealt with SATA drives, but I am buying a new computer, and the ability to mix them would make my life a million times easier.

---

### Post by tom.clements on 2007-05-11
> **Duck2006 said:**
> The problum is that grub is seeing three bootable devices on your system, so (hd0) (hd1) will not ghet you to boot windoze. Change your boot drive in your BOIS to boot the drive that has Linux on it and in your menu.lst add these lines to your windozes lines and see if it will work for you

map (hd0) (hd2)
map (hd2) (hd0)

thanks Duck.. but already tried that - that not working is what led me to try and get the ltldr work around going.

---

### Post by tom.clements on 2007-05-11
> **brennydoogles said:**
> This seems to suggest to me that you are able to mix IDE and SATA drives... is that true?? I have never dealt with SATA drives, but I am buying a new computer, and the ability to mix them would make my life a million times easier.

Yes I have had a system which both ide and sata working - in fac the sata drives were configured as a fake raid and I could read and wrtie the ntfs partition without problem (once I had a done a bit of config for the raid and also ntfs!). The point was that windows and linux resided side by side on the ide drive.

---

### Post by ipx on 2007-08-13
Have you gotten it working?

---

### Post by tom.clements on 2007-08-14
Unfortunately not.. given I have Ubuntu installed on a separate drive I just select the drive I want to boot in the bios boot menu. Works pretty well, its just annoying that it doesn't want to work properly with grub.

---

### Post by kafro on 2007-08-18
I have the same problem but i am totally lost.

---

### Post by jingo811 on 2007-08-18
> I'm not entirely sure what my next move might be.. am tempted to make the ubuntu drive the first one, windows the 2nd and then putting grub on the mbr of the ubuntu disc (which would now be the first) and then using map to try and boot windows.


I have done my Dual Boots like this for 5 years and liking it.  Installing Win XP first then Ubuntu letting Ubu decide for itself where it wants to put GRUB.  Until this day I don't know for sure where it is, it has simply worked for me. :)
[IMG]http://i16.tinypic.com/61lbnh1.png[/IMG]

Scroll to middle of my notes to read more about it.  Might not solve your complicated SATA problems though.  
However I read somewhere that you can only have 4 primary partitions for your boots maybe your Win XP has fallen out of those 4 primaries and is only 1 of many logical partitions.
[http://virtualseafarer.com/renaissance/allsparks/chapter4.html#ch4](http://virtualseafarer.com/renaissance/allsparks/chapter4.html#ch4)

---

### Post by Wynne G Oldman on 2007-08-18
An easy way to avoid this sort of problem is to install each operating system independently on it's own drive. By this I mean install Windows on a drive, without any other drives in the system. Do the same with Ubuntu. Then install both drives in your system, and choose which one to boot from in the BIOS. The advantage of using this method is that if you mess up one operating system, it won't effect the other one, as they're totally independent of each other.

---

### Post by stdPikachu on 2008-01-19
Heh, didn't think I'd find myself posting in Tom's thread (hi Tom!) but here I am.

Am also running into this problem, but it's made simpler/more complicated via the fact I only have the one hard drive in this machine, a laptop. Whenever I try to boot windows it too hangs on "Starting up ..." (have we verified whether this is a GRUB error message or not?), no disc activity etc. The only oddness I can see about this is that the XP install was cloned from another laptop via partimage and subsequently blown onto the new drive.

Partition layout as follows:
```
std@benedick:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ab921

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           8       64228+  83  Linux
/dev/sda2   *           9        3473    27832612+   7  HPFS/NTFS
/dev/sda3            3474        4496     8217247+  83  Linux
/dev/sda4            4497       30401   208081912+   5  Extended
/dev/sda5            4497        5895    11237436   83  Linux
/dev/sda6            5896       30156   194876451    b  W95 FAT32
/dev/sda7           30157       30401     1967931   82  Linux swap / Solaris
```

I've tried editing the old boot.ini on sda2 to point at the correct partition but neither option seems to work (does anyone know what schema boot.ini uses? It does number partitions from 1 rather than 0, right? In any case, setting the partition to 0, 1 or 2 doesn't result in a bootable windows.
```
std@benedick:~$ cat /mnt/windows/boot.ini
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

Annoyingly enough, the windows disc doesn't want to boot on this machine for some reason so mucking about with the MBR isn't an option.

Hard drive enumeration certainly seems to be my only problem with Ubuntu as of late...

---

