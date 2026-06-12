---
title: "Desperation Post.  Read Windows ME registry?"
date: 2011-06-16
forum: Any Other OS
---

### Post by npaisnel on 2011-06-16
Hi.  Total long shot here, am clutching at straws, but someone may have an idea. 

I'll post the question first and then an explanation of why this is needed next

We need to extract the Win ME installation serial number from a non running ME install, and then re install using the same serial number...So I beleive we will need to read the system.dat and another file or two, to find it, and then may need hacking a Win ME installation disk to allow install using the same serial number.



The background:

As someone who is always called on when things go wrong, I have been asked by work to get an old Dell PII laptop with Win ME running again.  It was working and then  "it would not boot"  And typically they never did any disk images or backups of any sort

The machine has only one purpose, to download engine data from an aircraft engine management system.

The software only runs with a hardware dongle that plugs in to the old Printer port

They do not have re install disks for the software.


The manufacturers will only supply new software if they can provide original purchase details or serial number, and it is not a new aircraft and none of this is available

The new software and will cost £31,000  

Do not even have an original Win ME disk...but have created a bootable one from a torrent d/load and a boot image

I have been told that if I do a re install of Windows over the top, and install using the original serial number, then all the original software registry entries are kept..it basically does a 'Repair install"

I have booted into Ubuntu, created a disk image and also extracted the original software program folder that was stored in the root.
This software will not run on any other machine, so i suspect that it is not a standalone exe. it was an install app, with all associated files and registry entries ...possibly hardware specific too.


When ME boots I have forced a bootlog text file, and the kernel was crashing and terminating within a few lines.  Bootlog.txt file was less than two pages long....I have fixed a load of issues, by restoring backup copies of kernel and other files from the Options /Cabs files on the HDD and now it boots and loads many files/drivers etc...and the bootlog.txt file not runs to about 18 pages. But now hanging at a gdi32.dll error, that I cnat seem to get around.


The next possible fix was to try a re install using the original serial number, so need to extract that somehow and try an re install

---

### Post by mips on 2011-06-16
Just to clarify, do you need to recover the WinME license key or the serial number for the aircraft engine management software?

You would be interested in the files below:
[http://en.wikipedia.org/wiki/Windows_Registry#Windows_95.2C_98.2C_and_Me](http://en.wikipedia.org/wiki/Windows_Registry#Windows_95.2C_98.2C_and_Me)
> Windows 95, 98, and Me
The registry files are named USER.DAT and SYSTEM.DAT are stored in the %WINDIR% directory. In Windows Me, Classes.dat was added. Also, each user profile (if profiles are enabled) has its own USER.DAT in profile's directory.

---

### Post by LowSky on 2011-06-16
Are you sure there isn't a sticker on the bottom of the PC with the key?

---

### Post by npaisnel on 2011-06-16
> **mips said:**
> Just to clarify, do you need to recover the WinME license key or the serial number for the aircraft engine management software?

You would be interested in the files below:
[http://en.wikipedia.org/wiki/Windows_Registry#Windows_95.2C_98.2C_and_Me](http://en.wikipedia.org/wiki/Windows_Registry#Windows_95.2C_98.2C_and_Me)


Well was only thinking of the Wind ME key to try a re install..but if I coudl extract the software key too, then that would be a bonus..and another angle on the problem.

Thanks for reminding my about the names of the .dat files...Classes.dat was added in ME if I remember correctly as a new registry file to oveercome some limit where windos would not load a registry file bigger than ...11Mb..was it..anyway not important

Pretty sure there are no profiles, just the one admin user

> 
Are you sure there isn't a sticker on the bottom of the PC with the key?


Doh!! slap me stupid...did not even think to look...They can sweat it out over the weekend.  I am day off tomorrow, ...and Monday..I'lll check that on Tuesday...so easy to overlook the obvious...cheers

---

### Post by halibaitor on 2011-06-16
Just a random thought.  Prior to doing anything else... Perhaps you should clone the whole drive so you could start over again in case of a mishap.

---

### Post by mips on 2011-06-16
> **halibaitor said:**
> Just a random thought.  Prior to doing anything else... Perhaps you should clone the whole drive so you could start over again in case of a mishap.

> **npaisnel said:**
> 
I have booted into Ubuntu, **created a disk image** and **also extracted the original software program folder** that was stored in the root.

.

---

### Post by npaisnel on 2011-06-16
Yes, thanks for the thought, but yes, already did an image..in fact did a couple, one after a Ubuntu live CD boot, and also using 'Acronis Dsk Image'

I did not get to it before early on...which was a shame...If i had done, I would have had it backed up before this problem even occurred...but as usual this sort of thing is never thought of till it is too late. then it is disaster recover situation.

Am very tempted to say 'Stuff it' not my problem...but it is now a matter of pride...not that Work will recognise any of my efforts for this  :(

---

### Post by Elfy on 2011-06-16
Thread moved to Other OS/Distro Talk.

---

### Post by npaisnel on 2011-06-16
Hey, thanks for moving the post..totally missed the "Other OS " sub forum

Cheers

---

### Post by BrokenKingpin on 2011-06-21
You could try [http://www.pcregedit.com/](http://www.pcregedit.com/) for getting the registry keys. That is a Linux live CD.

---

### Post by npaisnel on 2011-06-21
Ooooo...that is NICE...d/loading now

I could fins lots of other uses for that one :)
:popcorn:

---

