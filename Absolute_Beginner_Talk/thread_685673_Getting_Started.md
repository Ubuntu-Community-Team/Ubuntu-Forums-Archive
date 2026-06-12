---
title: "Getting Started"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by paul77 on 2008-02-02
Hi

I 'm trying to load Ubantu linux onto my XP PC mainly to try out  bash shell scripting. I have download Desktop Edition Ubuntu 7.10
from:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and then used Nero 7 to write the ubantu load to CD (double clicked
on the application downloaded from the above site and Nero was launched).

I assumed that if I left the CD in the disk drive and rebooted it would
bring up ubantu but it does'nt. I get a ubantu banner advertising 
Firefox and open office and no obvious way of running up ubantu.

Is one supposed to intervene in the windows boot process to make it
bring up linux instead. I don't wish to alter XP or replace it I just wish
to get access to linux (desktop) on an ad-hoc basis.

Can someone inform me as to how to get going?

Thanks
Paul

---

### Post by appleimac on 2008-02-02
Have you burnt the cd correctly?

---

### Post by legend2440 on 2008-02-02
Did you go into the BIOS setup and select the Boot from CD option?

If you open the CD are there a bunch of files or just the .iso file?

---

### Post by amazingtaters on 2008-02-02
You need to change your bios settings to boot from the cd drive first. That should clear it up, assuming you burnt the cd properly.

---

### Post by alwiap on 2008-02-02
hi,

make sure you have your CD-ROM enabled to boot in your BIOS.  When you restart you should see something like 'Hit F1 to enter setup' or something like that (the key differs on different computers), and put your CD-ROM to boot.  then you should be able to load the live-CD environment.

---

### Post by fiddledd on 2008-02-02
> **legend2440 said:**
> Did you go into the BIOS setup and select the Boot from CD option?

If you open the CD are there a bunch of files or just the .iso file?

If it booted which it sounds like it did, then BIOS must be setup OK, and he must have burned the image correctly :)
It's quite spooky really, makes no sense to me at all.
I'd suggest burning another cd and rechecking the md5sum beforehand.
If all that fails redownload the ios because the CD should boot into the Livecd desktop automatically.

---

### Post by amazingtaters on 2008-02-02
> **fiddledd said:**
> If it booted which it sounds like it did, then BIOS must be setup OK, and he must have burned the image correctly :)
It's quite spooky really, makes no sense to me at all.
I'd suggest burning another cd and rechecking the md5sum beforehand.
If all that fails redownload the ios because the CD should boot into the Livecd desktop automatically.

I think what he means is that in Windows it comes up with an Ubuntu banner and OSS software reccomendations. This is normal for an Ubuntu disc if you try to open it while logged in to Windows.

---

### Post by fiddledd on 2008-02-02
> **amazingtaters said:**
> I think what he means is that in Windows it comes up with an Ubuntu banner and OSS software reccomendations. This is normal for an Ubuntu disc if you try to open it while logged in to Windows.

Oh, I never knew that, not so spooky now. :)

---

### Post by fiddledd on 2008-02-02
Just to elaborate, the reason I never knew about the Ubuntu CD in Windows is I have AutoRun disabled for Removable Devices, so after burning the CD nothing happens on my System.

---

### Post by paul77 on 2008-02-03
Hi

XP was coming up and after double clicking on the CD drive ubantu icon the CD browser was launched 
and  I was getting the ubantu 7.10  (disk tree) banner where it says:

Boot from CD to try Ubantu without affecting your system
(plus OSS system recommendations)

I've since tried rebooting and holding down the following keys:-

F8...puts you into safe-mode 
F1...windows comes up
tab...a different screen then windows comes up
esc...windows comes up
del...cmos setup utility


With del I went into the advanced bios features (says it covers "virus protection, boot sequence") from the
cmos setup utiliuty screen expecting to see an option for 'boot from CD' but there was'nt one

I must be on the right track but something is not quite right!

Does anyone know what else is needed to get boot from CD to work? 


Thanks
Paul

ps the PC is a Fujitsu Siemens

---

### Post by legend2440 on 2008-02-03
This might help

[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

Where you see Boot Device Priority use + or - key to change priority

---

### Post by paul77 on 2008-02-03
Thanks it now works - put the CD disk in the DVD drawer (top drive) and changed the 1st boot drive bios setting from Floppy to CDROM and the restart brought up linux. Impressive.

It all seems to work the only problem I'm having is using Firefox - does anyone know how you 
make the initial connection to the internet - Firefox works but it has no connection.

:)

---

