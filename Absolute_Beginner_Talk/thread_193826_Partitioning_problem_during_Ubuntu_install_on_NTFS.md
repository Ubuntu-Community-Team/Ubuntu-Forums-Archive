---
title: "Partitioning problem during Ubuntu install on NTFS, dont know how to reformat either"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Fringe on 2006-06-10
(winded explaination, bear with me) To start I'm a complete newbie to Linux. I've been a Windows user for 6 years and previous had a different computer with FAT32 and could easily reformat it with Windows 98 boot disk with a simple "format C:" in the DOS command.

A few months ago I purchased a custom built computer with these stats (among common components like ethernet, soundcard, etc):

-Pentium 4 Processor 506, LGA775 Pkg 2.66GHz L2-Cache, 533 MHz FSB (EM64T -- supports 64-bit computing)
-80GB Seagate Hard Drive
-ATI Radeon AX300SE 128MB DDR (graphics card)
-MSI Motherboard, 915P Combo-FR, 915P+ICH6, DDR1+DDR2, ATX
-Windows XP Professional 64-bit Edition (preinstalled, no disk)

I began with just accepting Windows XP as I always have but ended up getting viruses, as always, among other things. I walked out of the room for an hour and came back and all heck broke loose on my computer and for some unknown reason I couldn't get Windows to work again. (don't ask)

So, I decided to heck with Windows anyway, I wanted to try Linux and had some Ubuntu 5.10 discs that I never used before. So I installed it, without reformating (since I couldn't get it format with my Windows 98 boot disk), and everything went well. I was running Ubuntu 5.10 on my computer and saw that it needed to update, so I downloaded the updates through the icon on my taskbar (if that's what it's called). After the download completed and tried installing, my computer froze. I saw some of the updates take place, such as my recycle bin icon changing as well as my wallpaper but I couldn't click anything and after almost an hour of just sitting there waiting for something to happen and be able to move the mouse or be able to access anything, I decided it was frozen.. simple as that..

Ever since then I get this messege on start-up:

GRUB Loading stage1.5.

GRUB Loading, please wait
Error 22

Anyway, so I tried to install the Ubuntu 5.10 again like I did before, without reformating, and it always messed during the partitioning. I'm not experienced with partitioning but I removed the Ubuntu CD and put my Windows 98 boot disk in again, and typed "fdisk", bringing up my partitioning info. I know nothing of how to 'unmount' (a term i've heard) or anything like that. I just deleted both the logical and ext partitions, in hope of putting the Ubuntu CD back in for a clean install. It did the same thing, error on the partitioning part.

I'm just hoping if I can reformat my harddrive, it will remove everything and I can start new, without any previous errors reoccuring from all my partitioning mishaps. 

So back to the formating. Everytime I try formating my harddrive with "format C:" using my Windows 98 boot disk, and also a Windows ME boot disk (didnt know if there was a different so I tried both) they both say "format C: not supported on drive". The very first time I tried though, it started to format, it went to 1% and after about half an hour it said something along the lines of "cannot fix error 22312... (something)" I can't remember exactly since it only did it once, everytime I tried formating afterwards it just said not supported.

As a note, whenever I put in either 98 or ME boot disk, they both say "no FAT32 partition on drive" and goes to give explainations as to way there isn't one. So, do I need a NTFS format disk in order to reformat my harddrive? I can't seem to find one, if there is.

My ultimate concern is just being able to install Ubuntu onto my computer. I tried installing other operating systems too, just to see if it was Ubuntu, but it wasn't. I tried Fox Linux, which doesn't even begin to install, I don't know if there's hardware compatibility or what. And I tried Zeta 1.1 (beOS) and it always freezes on the 'processor icon' during the load-up. So I'm thinking it's not compatible with my hardware too, seeing as it's a relatively young OS anyway.

SO, any ideas on how I can reformat my harddrive or set up partitions so that I can get Ubuntu to install correctly? Remember, it always gives me an error when it reaches the partitioning part of the Ubuntu installation. (Also, as a note, I ordered the Ubuntu 6.06 cds, 1 for pc, 1 for 64 bit and 1 for mac which haven't arrived yet) I'm hoping to install the 5.10 version I have right now until the new version arrives. If all goes well, by the end of this, I'll know how to reformat and have a clean install for a new OS (the 6.06, in this case).

That's it, I believe. Can't format with Windows boot disks, Ubuntu errors during partitioning section and ever since my failed update downloads when I actually had Ubuntu installed, it always get that GRUB loading error 22. Sorry for the long winded explanation but I want this to be fully understood so a solution can be cooked up. I really don't want to spend a hundred dollars taking it to a computer shop. If I can get this fixed myself, it will save me in the long run and give me the information I need to do it myself if this ever occurs again. But if all else fails, I'll end up taking it to the shop. So please, any help is appreciated and thank you in advance for reading this.

---

### Post by Kilz on 2006-06-10
[QUOTE=Fringe](winded explaination, bear with me) To start I'm a complete newbie to Linux. I've been a Windows user for 6 years and previous had a different computer with FAT32 and could easily reformat it with Windows 98 boot disk with a simple "format C:" in the DOS command.

A few months ago I purchased a custom built computer with these stats (among common components like ethernet, soundcard, etc):

-Pentium 4 Processor 506, LGA775 Pkg 2.66GHz L2-Cache, 533 MHz FSB (EM64T -- supports 64-bit computing)
-80GB Seagate Hard Drive
-ATI Radeon AX300SE 128MB DDR (graphics card)
-MSI Motherboard, 915P Combo-FR, 915P+ICH6, DDR1+DDR2, ATX
-Windows XP Professional 64-bit Edition (preinstalled, no disk)

I began with just accepting Windows XP as I always have but ended up getting viruses, as always, among other things. I walked out of the room for an hour and came back and all heck broke loose on my computer and for some unknown reason I couldn't get Windows to work again. (don't ask)

So, I decided to heck with Windows anyway, I wanted to try Linux and had some Ubuntu 5.10 discs that I never used before. So I installed it, without reformating (since I couldn't get it format with my Windows 98 boot disk), and everything went well. I was running Ubuntu 5.10 on my computer and saw that it needed to update, so I downloaded the updates through the icon on my taskbar (if that's what it's called). After the download completed and tried installing, my computer froze. I saw some of the updates take place, such as my recycle bin icon changing as well as my wallpaper but I couldn't click anything and after almost an hour of just sitting there waiting for something to happen and be able to move the mouse or be able to access anything, I decided it was frozen.. simple as that..

Ever since then I get this messege on start-up:

GRUB Loading stage1.5.

GRUB Loading, please wait
Error 22

Anyway, so I tried to install the Ubuntu 5.10 again like I did before, without reformating, and it always messed during the partitioning. I'm not experienced with partitioning but I removed the Ubuntu CD and put my Windows 98 boot disk in again, and typed "fdisk", bringing up my partitioning info. I know nothing of how to 'unmount' (a term i've heard) or anything like that. I just deleted both the logical and ext partitions, in hope of putting the Ubuntu CD back in for a clean install. It did the same thing, error on the partitioning part.

I'm just hoping if I can reformat my harddrive, it will remove everything and I can start new, without any previous errors reoccuring from all my partitioning mishaps. 

So back to the formating. Everytime I try formating my harddrive with "format C:" using my Windows 98 boot disk, and also a Windows ME boot disk (didnt know if there was a different so I tried both) they both say "format C: not supported on drive". The very first time I tried though, it started to format, it went to 1% and after about half an hour it said something along the lines of "cannot fix error 22312... (something)" I can't remember exactly since it only did it once, everytime I tried formating afterwards it just said not supported.

As a note, whenever I put in either 98 or ME boot disk, they both say "no FAT32 partition on drive" and goes to give explainations as to way there isn't one. So, do I need a NTFS format disk in order to reformat my harddrive? I can't seem to find one, if there is.

My ultimate concern is just being able to install Ubuntu onto my computer. I tried installing other operating systems too, just to see if it was Ubuntu, but it wasn't. I tried Fox Linux, which doesn't even begin to install, I don't know if there's hardware compatibility or what. And I tried Zeta 1.1 (beOS) and it always freezes on the 'processor icon' during the load-up. So I'm thinking it's not compatible with my hardware too, seeing as it's a relatively young OS anyway.

SO, any ideas on how I can reformat my harddrive or set up partitions so that I can get Ubuntu to install correctly? Remember, it always gives me an error when it reaches the partitioning part of the Ubuntu installation. (Also, as a note, I ordered the Ubuntu 6.06 cds, 1 for pc, 1 for 64 bit and 1 for mac which haven't arrived yet) I'm hoping to install the 5.10 version I have right now until the new version arrives. If all goes well, by the end of this, I'll know how to reformat and have a clean install for a new OS (the 6.06, in this case).

That's it, I believe. Can't format with Windows boot disks, Ubuntu errors during partitioning section and ever since my failed update downloads when I actually had Ubuntu installed, it always get that GRUB loading error 22. Sorry for the long winded explanation but I want this to be fully understood so a solution can be cooked up. I really don't want to spend a hundred dollars taking it to a computer shop. If I can get this fixed myself, it will save me in the long run and give me the information I need to do it myself if this ever occurs again. But if all else fails, I'll end up taking it to the shop. So please, any help is appreciated and thank you in advance for reading this.[/QUOTE]

What errors do you get during patitioning?

---

### Post by dglock on 2006-06-10
First thing, linux, and ubunt do not install on a fat32 or ntfs partiton.  The reason your windows boot disks won't work is they can't or won't see a linux partiton.

  If you had ubuntu installed then its on a ext3 or reiserfs partiton, not ntfs. You can, either get the tools floppy from the web site of your drive or use partiton magic to clean up the drive. The tools disk is free, partiton magic is not.

don

---

### Post by PhilOSparta on 2006-06-10
While running the 5.10 install CD, tell the partition section to use the entire drive. ( Assuming that you have nothing to lose.) I believe that the 5.10 installer doesn't want to load over an existing system unless you tell it that you want the entire drive to be used.  Since you have already installed Ubuntu 5.10 you want to over write the whole thing.

The partitioning section of that version of Ubuntu was a little intimidating.  You need to tell it where to mount root i.e.  /    .

You will be real happy when you finally see the Dapper 6.06 version.  Really slick!

---

### Post by KarmaKing on 2006-06-10
hello Fringe,

try this website that aysiu pointed me to

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by KarmaKing on 2006-06-10
matter of fact got to this page here and 1/3 of the way down it discusses the error you speak of

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Fringe on 2006-06-11
[QUOTE=Kilz]What errors do you get during patitioning?[/QUOTE]

I seem to get errors in different places everytime I try. This time, instead of during the partition, I often get errors during installing the base system. I tried 3 times this morning and here's each problem that occured.

1st try:
[!!] Install Base System
Installation Step Failed
An installation step failed. You can try to run the failing step again from the menu, or skip it and choose something else. The failing step is: install the base system.

I just went back to partitioning step and it showed:

#1 primary 78.5GB (shows some lightning bolt and what looks like a skull) ext3 /
#5 logical 1.5GB (shows that same skull thing) swap   swap

I clicked finish.

It went through with the installation and rebooted my machine after ejecting the CD-ROM.

After reboot it said OK to all the settings at the beginning and begin to install the packages. At 44% configuring gstream0.8-jpeg had an error that said a lot of numbers that repeated about 7 times and then disabled for 5 minutes. I didn't wait the 5 minutes and restarted manually to see if it would do it all over again. It didn't, it said it couldn't find a bunch of files and so I redid the installation process again.


2nd try:
All was the same, said error during install the base system and I went back and clicked partition again, clicked Finish on the settings showed (same as above) and the installation went through yet again, rebooting the system after ejecting the CD-ROM.

This time it had an error at 53% something involving python. I wrote down the error this time:

open: Read-only file system
/usr/sbin/termwrap: line 140: $tmpfile:ambiguous redirect
/usr/sbin/base-config: line 31: /var/log/base-config.timings: Read-only file system
(it repeated this 7 times and then said:

* Id "1" respawning too fast: disabled for 5 minutes)

I waited 5 minutes and it said the same lines about 14 times this time and then said the disabled for 5 minutes thing again.


NOW my computer shows this error messege during startup:

MSI              Live Update 2

915/G Combo A7058IMS V1.4 09/14/04
Intel (R) Pentium (R) 4 PCU, Speed: 133x20=2666MHz
DDR Speed=333MHz, Single-Channel
512MB OK

Auto-Detecting Pri Master..IDE Hard Disk: WDC WD800JB-00E7A0 77.07W77
Auto-Detecting 3rd Master..ATAPI CDROM:_NEC DVDRW .VD3540A 1.01
Auto-detecting USB Mass Storage Devices...
Checking NVRAM

Pri Master Hard Disk: S.M.A.R.T. Status BAD, Backup and Replace
Press F1 to Resume

(did something just screw up my hard drive???)


3rd try:
Same as abovebut this time at 57% on libxm12. It kept repeating lines over and over and gave the disabled for 5 minutes thing.

Now, this process takes a while for the whole install thing.. and I've gotten a bit impatient with retrying over and over so I thought I'd stop now and see if anyone knew what I was doing wrong..  Does anyone think there's something wrong with my hardware that causes the error during installation.. it seems to happen at different places each time. I thought maybe it was the CD so I tried a different one (since they sent me 5 of the same) for the third try and it still gave me an error during different place, as stated above.

---

### Post by Fringe on 2006-06-11
[QUOTE=dglock]First thing, linux, and ubunt do not install on a fat32 or ntfs partiton.  The reason your windows boot disks won't work is they can't or won't see a linux partiton.

  If you had ubuntu installed then its on a ext3 or reiserfs partiton, not ntfs. You can, either get the tools floppy from the web site of your drive or use partiton magic to clean up the drive. The tools disk is free, partiton magic is not.

don[/QUOTE]

Ah yes, I noticed it said ext3, not NTFS. My mistake. I dont know much about partitions and when I bought the computer it said NTFS, so I thought that's what it was. Probably was when Windows as on it but not after the first Linux installation I made earlier. I went to the Seagate website to download their tools disk and after saving it to my computer and then setting it up through their steps to put it on my floppy, I put it in my computer and it just showed "Seagate" logo and had the flashing line waiting for a command. I didn't know what to type..  their website said to check the readme file on the disk but I couldn't find it when I opened it on this computer using the folder explorer. Just a bunch of .exe's.. nothing saying readme anywhere and I typed "readme" on the command thing on my screwed up computer but it said bad command. Any idea on how to get this tools disk to work?

---

### Post by Fringe on 2006-06-11
[QUOTE=KarmaKing]matter of fact got to this page here and 1/3 of the way down it discusses the error you speak of

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)[/QUOTE]

Well that error is gone now, read the reply I made a couple comments up about the steps I went through. I can't seem to get it to finish the installation after the install reboot. It will show the Ubuntu loading screen and say OK to everything up until the root file and then say it cannot find files, among other numbers that were far too much to write out--lots of directories and whatnot.  Everytime I try to reinstall it errors during different places! :(  I might have to take it to the shop to save my hair from falling out, Haha.

---

### Post by Fringe on 2006-06-11
[QUOTE=PhilOSparta]While running the 5.10 install CD, tell the partition section to use the entire drive. ( Assuming that you have nothing to lose.) I believe that the 5.10 installer doesn't want to load over an existing system unless you tell it that you want the entire drive to be used.  Since you have already installed Ubuntu 5.10 you want to over write the whole thing.

The partitioning section of that version of Ubuntu was a little intimidating.  You need to tell it where to mount root i.e.  /    .

You will be real happy when you finally see the Dapper 6.06 version.  Really slick![/QUOTE]

I selected the Erase entire disk option, which was the top option. The second one said Erase entire disk and use LVM.. I didn't know what LVM is so I didn't select it. It would work and then error during installing the base. I would go back a step to the partitioning and simply select "Finish" when it showed what partitions it was making. (As stated in other reply I made, it would show the etc3   /   partition and a swap partition) The install would go well until the reboot when it would try to configure and install the packages, after the Ubuntu loading screen. It will freeze in different places everytime, 44%, 53%, 57%.. etc.  I stopped after the third try, assuming it would continue the cycle. But the numbers seem to be getting larger.. maybe if I keep doing it, it will eventually get to 100%? Haha. Oh well.. I might end up just waiting a month or so until the Dapper 6.06 CDs come in and hope the installation goes more smooth than the 5.10 Breezy.  *Crosses Fingers*

---

### Post by Fringe on 2006-06-13
Okay, after about 20 attempted installations, it finally worked. Don't ask me how.. I did the same thing every time and it just happened to work all of a sudden. Thanks for all your help everyone!

---

