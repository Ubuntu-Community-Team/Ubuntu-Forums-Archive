---
title: "Can't install: Error reading boot CD"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by TheSarge on 2007-03-14
Need some help.
I'm trying to install Ubuntu 6.10 (ubuntu-6.10-desktop-i386.iso) to my old Celeron machine, but every time I boot from the burned CD, I get:

Loading isolinux: Disk error 10, AX = 4200,  Drive EF
I/O Error
Error reading boot CD
Reboot

What am I doing wrong?

The system in trying to install to has specs as follows:

CPU: Intel Celeron 1.20 GHz (FC-PGA)
Mainboard: MSI 694T Pro
RAM: 512 MB SDRAM
Video: ATI Radeon 9200SE (AGP 8x)
Optical drive: LG HL-DT-ST DVDRAM GSA 4082B
Hard Drive: 80 GB WD Caviar IDE


Please help :confused:

---

### Post by orkim on 2007-03-14
Typically this is due to bad or dirty media.  You might try burning on a different brand of CD-R's or at a slower speed.  The slower speed will actually give you a better burn because the CD spins slower and isn't allowed to "drift" as much while it's being burnt.

I hope that helps.  Please let us know!

-orkim

---

### Post by DaveyG on 2007-03-14
Also depends on what software you used to burn the image...

---

### Post by TheSarge on 2007-03-14
There's nothing wrong with the media. These are regular CD-Rs, nothing wrong with them. To be sure, I bruned multiple copies and I get the exact same error regarless of which disk I put in.


And I used InfraRec to burn these disks.
And then I tried Nero
And then I tried BurnAtOnce.

No difference.


The thing is, I can install copies of Windows XP, Windows 2000 and Windows 2003 on that machine, but when I try and install Ubuantu using CD-Rs from the same spindle burned & burned from the same burner... I get the above error. 
*Whiskey Tango Foxtrot Interrogative*:confused: :mad:

---

### Post by undertakingyou on 2007-03-14
What was the burn speed?  I have been having the same thing with both feisty and edgy CD's but not dapper, but I had different CD-r brands.  Also, ubuntu is packing a lot more on the CD that windows is.  Why?  It is a live CD.

---

### Post by noob_saioke45601 on 2007-03-14
try using nero burning rom. then, selecting boot disc and selecting 4x as a burning speed. yes it will take awhile to burn but the first time i burned the disc it happened to me too.

---

### Post by orkim on 2007-03-14
In that regard, it may be some compiler specific flags that were used to build isolinux that your hardware setup doesn't like.  Have you been able to install any Linux distribution?

You might try installing Debian and then upgrade to Ubuntu.  You will only have to change your repositories and issue a "apt-get upgrade" if my memory serves me correct.  I believe there are several guides related to this on the forums.

I hop that helps!

-orkim

---

### Post by TheSarge on 2007-03-14
> **orkim said:**
> In that regard, it may be some compiler specific flags that were used to build isolinux that your hardware setup doesn't like.  Have you been able to install any Linux distribution?

You might try installing Debian and then upgrade to Ubuntu.  You will only have to change your repositories and issue a "apt-get upgrade" if my memory serves me correct.  I believe there are several guides related to this on the forums.

I hop that helps!

-orkim
Sorry, I'm a Linux virgin so I have no idea what the **** you're talking about. Thanks anyways. :lolflag: 

The optical drive can read the disk just fine. How do I know? The thing boots to the Ubuantu screen and asks me what I want to do. Then I choose "Start or install Ubuantu". Only then does Ubuantu decide it's got a problem.
I'll try burning again at 4x speed. Later :(

---

### Post by orkim on 2007-03-14
I think there may also be a safe mode installation that may help.  If you type help at that prompt or select it from the list that may help.  It's been ages since I have booted off the CD and I have a bad memory to begin with.

Good luck.

-orkim

---

### Post by TheSarge on 2007-03-14
Ok, none of that helped. The dam thing just doesn't like my hardware, apparantly.
So much for Ubuantu.:(

---

### Post by orkim on 2007-03-14
You might try a Debian install which can then "upgrade" to Ubuntu painlessly.  Just a suggestion.

-orkim

---

### Post by TheSarge on 2007-03-14
> **orkim said:**
> You might try a Debian install which can then "upgrade" to Ubuntu painlessly.  Just a suggestion.

-orkim

I might, if I knew what "Debian" was.
You know what? I just tried booting the damm thing off the same machine I burned the disk from. And it gave me a similar error (got further this time, but it never finished starting Ubuantu).
**** it. If they can't even write an installer that can boot without crashing on the same machine the disk was burned from then I'm not touching Ubuantu with a ten-foot pole. It's garbage as far as I'm concerned. :mad: 

Thanks for all your help.

---

### Post by orkim on 2007-03-14
Sorry to hear your troubles.  There are hundred of thousands of successful installations of Ubuntu world wide.  I'm sure if you stick with it you can figure out your problem.

Either way, best of luck to you.

-orkim

---

