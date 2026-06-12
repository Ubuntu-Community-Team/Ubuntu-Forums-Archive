---
title: "I got a legacy Mac"
date: 2005-02-15
forum: Apple PPC Users
---

### Post by Wolfton on 2005-02-15
I am currently experimenting with Ubuntu  \\:D/  and I wish to put it on a Macintosh WGS 7250/120.  I'm new to Ubuntu, but not so new to Red Hat.  I have tried YellowDog, but I had issues because I don't have a Mac OS 8.0 cd.  I tried to DL the 8.6, but its only an update.  I would really love to turn this little beige box into a Linux comp for my daughter.

Does anyone know how I can either obtain a MAC OS (between 7.5.5 and 8.6) on cd?  Can anyone tell me if that little Mac will even run Ubuntu?  Has anyone here ever installed Linux in a PPC and not needed a Mac OS CD?

My signature contains a link to the specs for my box.  Everything is stock, except the whopping 64mb of RAM (4 x pcs, 16mb each) and an extra HDD with 2.1GB (total 3.3 BG between the 2 HDDs)  If I can get Ubuntu and even MOL running on that machine, I'll probably upgrade to a G3 card and add USB to it. ](*,)

---

### Post by mac-mini-sweet-silence on 2005-02-15
Once upon a time I ran Debian 2.0 on a Pentium 200Mhz, with only 16 MB RAM. I even ran X on that, with a 2MB Matrox Mystique graphics card. So yes, it is possible, but maybe you should run something lighter than Gnome, e.g WindowMaker.  :-)

---

### Post by Wolfton on 2005-02-16
I only have Yellow Dog (don't know which version) and Ubuntu 4.3.  My big issue is that I am in Germany and I can't download this stuff on dialup.

I also have DeMuDi (another distribution that might be Mac-Compatible) but I haven't looked at it yet.  The CDs came on the cover of an issue of Linux User & Developer that I picked up last week. \\:D/ 

The question still stands though.  Do I really need the Mac OS CDs to load Linux?  Even if I don't care to use MOL?

---

### Post by toojays on 2005-02-16
On the so-called "Old World" Macs like the 7250, there are two ways to book Linux. One is with BootX, and the other is with Quik. Quik tends to be quite difficult to figure out, and so most distributions still use BootX. Unfortunately BootX requires you to boot into MacOS first.

So, to do it without MacOS, you need to find a Quik boot disk. I once heard of such a thing, but I'm not sure if it is real or not. Maybe you could find more information in the Debian list archives.

I used to run WindowMaker and Firefox on a G3/233 with 128 MB of RAM, and I that was quite a decent setup for my needs at the time. I could run movies and play music with no problems.

Good luck.

---

### Post by hndrcks on 2005-02-17
[QUOTE=Wolfton]
The question still stands though.  Do I really need the Mac OS CDs to load Linux?  Even if I don't care to use MOL?[/QUOTE]

Answer: probably. Read this page [http://www.biccard.com/alan/7200/7200boot.html](http://www.biccard.com/alan/7200/7200boot.html) and try that a couple times; then, when you are completely frustrated and decide BootX is a better idea read on...

This link [http://www.lowendmac.com/macos.shtml](http://www.lowendmac.com/macos.shtml) will give you the lowdown on what is freely available off the internet. Best bet for you is likely 7.5.3 with 7.5.5 update - this will run on a 7200 and will support BootX. It is about 15 floppies - so on reasonable dialup you can grab that in an hour or two. You might want to check the classifieds / Ebay in your area; a cd of OS8 is often available for a few dollars.

---

### Post by tormod on 2005-02-18
[QUOTE=Wolfton]I also have DeMuDi (another distribution that might be Mac-Compatible) but I haven't looked at it yet.  The CDs came on the cover of an issue of Linux User & Developer that I picked up last week. \\:D/ 
[/QUOTE]Demudi is great, I run it on my old beige G3. However no ppc Demudi cd has been released yet AFAIK. I installed Debian sarge and then added the Demudi stuff over the net. Sarge/demudi is much better than YDL, IMMO.
> The question still stands though.  Do I really need the Mac OS CDs to load Linux?  Even if I don't care to use MOL?It is very handy to have a bootable macos cd, when you start playing around...
Might save you a lot of hassle.

BTW, I try to get rid of some G3/400 upgrade cards (in Switzerland) if you're interested.
Tormod

---

### Post by DJ_Max on 2005-02-18
FYI, [http://penguinppc.org/bootloaders/quik/](http://penguinppc.org/bootloaders/quik/)

---

### Post by Wolfton on 2005-03-07
Well, I downloaded the OS 7.5* stuff, and unfirtunately, my Mac isn't starting up right now.  I don't know what I did, except maybe screwing up the YDL over a year and a half ago.  I moved the entire system from a 1.2GB HDD to a 2.1 GB HDD by dragging and dropping.  Now the box is temper-MENTAL at best when booting up.  I did this when I knew much less about computers than I do now, and I just dragged from one disk to the other.  Then I formated the old disk.  Before restarting, I did switch the boot to the new disk and everything worked fine for a while. 
After I spent a year away from it, with the computer boxed up in the basement, the thing didn't want to start up very well.  I think maybe I damaged something when I dismantled it and cleaned it.

As far as the 7.5.5 stuff goes, if they're compressed as sbin, how can I write them to floppy on a PC?  I can't just copy the files directly and boot form them.  That would be too simple.

I'll try my Ubuntu CD in the Mac. Maybe I'll get lucky and it'll work.

---

### Post by hndrcks on 2005-03-07
[QUOTE=Wolfton]As far as the 7.5.5 stuff goes, if they're compressed as sbin, how can I write them to floppy on a PC?[/QUOTE]

Aladdin Stuffit for PC

RaWrite

WinImage

All three can write mac floppies.

---

