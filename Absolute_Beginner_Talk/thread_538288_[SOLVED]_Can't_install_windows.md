---
title: "[SOLVED] Can't install windows"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by purdticker on 2007-08-29
Hey everyone,

When I try to install windows it says it can't find any hard disks.  I *know* this is a very common problem, but I've done what I've read in the other forums it just doesn't work!!

Here's what I've tried (attempted to install windows after each):
[LIST]
[*]Create a fat32 partition
[*]Delete ALL partitions
[*]Create NTFS partition
[/LIST]

After each of these attemps windows could never find any hard disks.

I've been booting from ubuntu install disk and running gparted to partition hard drives.

Am I doing something wrong?

---

### Post by oilchangeguy on 2007-08-29
if you're booting from the windows cd, and following the prompts correctly. then it's possible the hard drive has problems.

---

### Post by Richardky on 2007-08-29
fdisk the drive first ..

---

### Post by bobpur on 2007-08-29
You never said if it was a PATA drive (Wide flat ribbon cable) or SATA drive (1/2" wide cable).  
If it's a PATA drive check the jumper settings. If you have a SATA drive you have no jumpers. 
Maybe you need to get you another disc formatter thingy. Download Gparted from [www.distrowatch.com](www.distrowatch.com). There are a couple of others there as well, but Gparted worked for me if everything else was alright.
                                                                        Good Luck.

---

### Post by abhiroopb on 2007-08-29
> **bobpur said:**
> You never said if it was a PATA drive (Wide flat ribbon cable) or SATA drive (1/2" wide cable).  
If it's a PATA drive check the jumper settings. If you have a SATA drive you have no jumpers. 
Maybe you need to get you another disc formatter thingy. Download Gparted from [www.distrowatch.com](www.distrowatch.com). There are a couple of others there as well, but Gparted worked for me if everything else was alright.
                                                                        Good Luck.

From what I've heard SATA drives aren't recognised by XP. That could be the problem. I've actually been having a similar issue (thread: [http://ubuntuforums.org/showthread.php?t=537703](http://ubuntuforums.org/showthread.php?t=537703)) and I was thinking of using nliteos to put drivers, etc. on one cd. Could someone shed some light on nliteos and how I go about getting the required drivers.

---

### Post by abhiroopb on 2007-08-29
I think the HP drive I have is ATA-5, is that the same as SATA?

---

### Post by purdticker on 2007-08-29
I'm not sure what's in it... I'm working on a laptop, an HP dv9000

I tried fdisk, never used it before... I tried creating a new dos partition, writing changes and restarting, still can't find hard disks....

---

### Post by purdticker on 2007-08-29
Pretty sure it's not a hardware issue, I had windows installed on it like a week ago, went to ubuntu for a while, and just yesterday trying to dual boot, but I can't even install windows...

---

### Post by FuturePilot on 2007-08-29
Yes, if it's a SATA drive, you'll need to find drivers for it and get them on a floppy. Then you have to load them when you boot the Windows CD.

---

### Post by abhiroopb on 2007-08-29
Unfortunately it is most likely a hardware issue. The thing is the HP recovery partition solved the problem but I have deleted that (as I'm guessing you have). Whats the solution without a floppy?

---

### Post by purdticker on 2007-08-29
I don't even have a floppy drive!  Lol, who would've thought I'd actually need one... Any other way?

---

### Post by abhiroopb on 2007-08-29
So apparently it is possible to load the drivers using [http://www.nliteos.com/](http://www.nliteos.com/)

But I don't know what drivers to get or where to get them. And I don't even know how to use nliteos! I guess we'll have to wait for more experienced users!

---

### Post by purdticker on 2007-08-29
Apparently I can load these from a flash drive?

[http://www.ashbaughonline.com/2007/06/02/setup-did-not-find-any-hard-disk-drives-installed-in-your-computer/](http://www.ashbaughonline.com/2007/06/02/setup-did-not-find-any-hard-disk-drives-installed-in-your-computer/)

Going to try that... HP better have these drivers on their website!

---

### Post by abhiroopb on 2007-08-29
I read the comments but the guy said that it only works with a floppy drive. This sort of makes sense as in the setup menu (which is win95  I believe) it won't recognise the flash drive at all.

---

### Post by purdticker on 2007-08-29
Ugh, well in any case I don't see drivers on HP site... how do I found where I need to go to get the driver?

---

### Post by FuturePilot on 2007-08-29
purdticker,
You said you have an HP. Do you have backup CDs? Or even better, a recovery partition?

---

### Post by boogieboarder97 on 2007-08-29
you should dual boot it makes life easier but you shouldve left windows on in the first place then ran the ubuntu install because itll automatically setup the grub bootloader

---

### Post by purdticker on 2007-08-29
Nope, I completely reformatted and installed windows xp a long time ago (didn't have problems then). No more recovery disks or recovery partition.

---

### Post by purdticker on 2007-08-29
> **boogieboarder97 said:**
> you should dual boot it makes life easier but you shouldve left windows on in the first place then ran the ubuntu install because itll automatically setup the grub bootloader

Yup learning the hard way :)

---

### Post by abhiroopb on 2007-08-29
Unfortunately I deleted the partition as well. And I have the CDs but not with me. In any case the HP recovery partition is a bit of a pain. It basically erases everything and reformats. Erasing any other partition. In any case I'm not really looking for a windows partition as I'm quite happy with Ubuntu. I just want to load up a stripped down version of XP.

I swear I used to like HP but the hardware is SUCH a pain. First the matSHITa DVD dual layer drives slow don't work with copy-protected content (without changing the region), and now this crazy HD issue!

---

### Post by purdticker on 2007-08-29
Theoretically speaking, if I had a pirated copy of windows vista, it would install ok?

---

### Post by abhiroopb on 2007-08-29
> **purdticker said:**
> Theoretically speaking, if I had a pirated copy of windows vista, it would install ok?

I assume the problem with detection would be the same, although I don't know if vista detects SATA.

---

### Post by abhiroopb on 2007-08-29
Feel like cheering...

Found the HP driver:

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-39535-1&lc=en&cc=us&dlc=en&product=3223544&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-39535-1&lc=en&cc=us&dlc=en&product=3223544&os=228&lang=en)

check it out.

Now I just have to figure out how nLite works :)

If you have any luck let me know.

---

### Post by purdticker on 2007-08-29
I've read that it does... I'll let you know how that theoretically turns out :P

---

### Post by purdticker on 2007-08-29
> **abhiroopb said:**
> Feel like cheering...

Found the HP driver:

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-39535-1&lc=en&cc=us&dlc=en&product=3223544&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-39535-1&lc=en&cc=us&dlc=en&product=3223544&os=228&lang=en)

check it out.

Now I just have to figure out how nLite works :)

If you have any luck let me know.


Oh I love you :P  K I'll play around with nLite

---

### Post by abhiroopb on 2007-08-29
> **purdticker said:**
> Oh I love you :P  K I'll play around with nLite


A little too friendly but I share your joy. I'm at work, so tell me how it goes. 

I was reading the nLite guide and apparently when it comes to drivers they have to be inf files. This is an .exe file. So you'll have to figure out what to do about that!

---

### Post by FuturePilot on 2007-08-29
You should be able to open the .exe to extract the necessary files with a .rar archive app.

---

### Post by abhiroopb on 2007-08-29
Thanks! That was kind of important.

Last thing. Well a few of things really. 

1. Will nLite support the modified version of XP I downloaded? I'm assuming it would because all nLite requires is that I copy all the files on the CD onto the HD.

2. By loading the SATA driver where nLite tells you to load drivers will it work? What I mean is when the setup is starting will the installation detect the SATA driver?

3. I have a program (called GameXP) that apparently tweaks your XP settings to make it easy to play games can I integrate this into it as well?

4. I'm planning on running a purely gaming version of XP, so I don't even intend to have internet. So ideally I don't want to have to download any of the service packs or hotfixes, would you say that these are recommended?

Cheers!

---

### Post by purdticker on 2007-08-29
Ugh, apparently nLite can only be run on windows!

Requires .net framework, won't work with wine

---

### Post by abhiroopb on 2007-08-29
Damn thats a pain! My parents have a mac with parallels I thought I'd use that...

I also mailed HP and I got a response (in 30 mins!):

Please follow the steps to disable sata native support.

Enter the system BIOS

1. Press and hold the Power button for 5 Seconds to turn off the PC.
2. Tap the F10 key while you press the Power button to turn on the PC.
Release the F10 key after text is displayed on the screen of the PC.
3. Go to System Configuration
4. Choose "SATA Native Support" and "DISABLE" it.
5. Save settings and Exit.

Once the sata native support is disabled you will be able to install xp
pro on your notebook.

This seems to be a relatively simple way. Compared to slip-streaming, etc.

Who says HP customer support is rubbish? Perhaps if you have to take in the laptop, but I am highly impressed by such a quick response.

I'd appreciate it if you could try out this method purdticker, if it works then I can go ahead with it as well. Otherwise let me know the problem and I'll mail the guy back.

---

### Post by purdticker on 2007-08-29
I ran wine with this file and it asked for floppy :/

Next I tried extracting the file.  First I did:

> 
:~/Desktop/SATA$ cabextract  sp32478.exe
Extracting cabinet:  sp32478.exe
  extracting F6flpy32.exe

All done, no errors.


Then, I tried again with extracted exe.
> :~/Desktop/SATA$ cabextract F6flpy32.exe 
F6flpy32.exe: no valid cabinets found

All done, errors in processing 1 file(s)

That also failed... Note that this file is called F6flpy32.exe.... flpy = floppy?  I don't have a floppy...

---

### Post by purdticker on 2007-08-29
> **abhiroopb said:**
> I'd appreciate it if you could try out this method purdticker, if it works then I can go ahead with it as well. Otherwise let me know the problem and I'll mail the guy back.

I'll try that now, but what affects will disabling the native support have on the system?

---

### Post by purdticker on 2007-08-29
Disabling SATA works, installing XP now...

---

### Post by FuturePilot on 2007-08-30
Just make sure you install the driver after installing XP and then enable the native SATA support. It's not really meant to run with that disabled for a long time. Basically it's a workaround for your problem until you can get the driver installed.

---

### Post by abhiroopb on 2007-08-30
> **purdticker said:**
> Disabling SATA works, installing XP now...

Good to know it worked :). Will mail them and let them know.

Also I wonder I'll ask them if it is neccessary to re-enable support since the support guy didn't mention that.

---

### Post by abhiroopb on 2007-08-30
Also I notice that this is a big issue and most posters recommend the floppy disk method. IS there any way for people to come to this thread if they have the same problem? The disabling method seems to be the most painless and yet no-one has yet mentioned it.

---

### Post by abhiroopb on 2007-08-30
LAST thing: How does the grub boot loader function? You see I plan on installing XP on the complete HD. Then I plan on using a systemrescue cd loading gparted and making an ext3 partition. Then I will reload the image of Ubuntu that I already have. The issue is what happens on boot? Does grub start up and let me choose between ubuntu and xp?

---

### Post by abhiroopb on 2007-08-30
Got sent to this link when I asked about SATA native support:

[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00758841](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c00758841)


check it out, don't understand the point of it but still worth a read I guess. Best thing though is just to install xp and install the .exe driver for sata and then re-enable support.

---

### Post by Frazer on 2007-09-22
I have the files nlite needs to do this, if anyone is still looking for them I can send them to you.  Yes nlite needs to be run on windows

hypothetically I think Vista should work but VISTA IS TRULY HORRIBLE especially for games, Im still stuck in XP for now because I have an ATI card and cant get my games to work on wine.

There is a version of nlite that works on vista but dunno if it could make it any good.  Maybe you can remove everything new exept direct X 10?  Personally I went out and bought a nintendo wii (its well cool) and when I get fed up with RF Online on windows im ditching it totally.

---

