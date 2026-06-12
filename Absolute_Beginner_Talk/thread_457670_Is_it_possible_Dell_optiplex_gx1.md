---
title: "Is it possible? Dell optiplex gx1"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by totalnub on 2007-05-28
well, i need you guys to give me some feedback on whether or not ubuntu/xubuntu would work on this machine. [http://docs.us.dell.com/support/edocs/systems/ban_gx1/specs.htm](http://docs.us.dell.com/support/edocs/systems/ban_gx1/specs.htm)
i found one with no ram or hdd. i am wondering if anyone has tried this type of machine and whether or not booting from a cd works......any help is appreciated.

---

### Post by totalnub on 2007-05-28
i also came across one of these [http://support.dell.com/support/edocs/systems/opgx110/en/ug/specs.htm....same](http://support.dell.com/support/edocs/systems/opgx110/en/ug/specs.htm....same) situation applies...no ram/hdd. any hope?

---

### Post by mattva01 on 2007-05-28
Well I'm helping with a project to distribute these exact computers to low-income families in the DC area.
They run Ubuntu great with 256 megs of ram. Less than that though and they need Xubuntu.
EDIT: They are Pentium 3  450 MHz.

---

### Post by wolfear on 2007-05-30
The GX1 is, IMHO, the best "workhorse" system. It'll take pretty much whatever you throw at it and just keep on trucking.

I currently run an Optiplex GX 1 with the original slot 1, 333/100fsb cpu and around 400m ram (not sure of exact right now), dual HDD (the original 6gig that came with the system plus a 7 gig I had laying around), 2 CD drives (1 add-on CDR-W and original CD drive).
The spec sheets say I am running the Rev 2 mobo, but the jumper setting top at 500mh (instead of the 550 or 600 which, I think, the Rev 2 is supposed to have), so not sure

I have, at various times, run various combinations of 6.06 or 6,10 server only, 6.06 server with Gnome or KDE desktop, standard Ubuntu/Kubuntu desktops only and dual booted various combinations of the above with WinXP.
I found after switching to Ubuntu I had a much faster system (whether this is actual or I am just able to work more efficiently I have never tested).

Booting from a standard CD has never been a problem, but it gets a bit twitchy every now and then if using a CDR-W (CDR works fine) in the original CD Drive (the CDR-W I added will boot from anything). This is most likely due to the drive itself rather than the system.

From what I remember, (and I could be wrong, I've slept since I last checked..lol):
Rev 2 mobos are, in theory, supposed to support up to 600 mhz/100FSB  in the original slot1 cpus and up to about 1200 mhz with a  socket (? not 100% which socket, but I think it was 7 ?) adapter that will clock down to 100 FSB.
Rev 1 mobos, I think, top out at 450mhz/100 FSB and won't work with an adapter.
Both are locked in at 100FSB max, and cannot be clocked up (found this out the hard way when I ordered a 600 mhz cpu to upgrade and found out it was a 133 FSB)

I have heard of people running 1+ gig ram, but I am quite happy with mine so don't see the need to spend the $$$ if I don't need to.

The BIOS can be a bit touchy at times, so make sure the system is Rev A07 (the system takes a BIOS flash very nicely).

Hope some of this helps and I didn't ramble too much.

---

### Post by sTpny on 2008-01-24
I have a Dell OptiPlex GX1 running with ubuntu on it. It runs just fine, but it doesn't install with sound or support for 3d graphics. For sound, you'll need to add the line snd-cs4236 to your /etc/modules file. The 3d graphics I haven't figured out yet, but I know others have gotten it to work.  It also boots gutsy gibbon saying that "the bios (1999) fails cutoff age (2000) acpi=force is required to enable acpi.", and I'm not quite sure yet where to put that. Without it, none of the computers advanced power saving features will work.  This was a little strange, since feisty faun had them all enabled after install. (it was actually the first time any operating system was able to put this computer to sleep. 

I'm thinking that rather than adding acpi=force, a better solution is flashing the bios with an update, which I see from our friends post is supposed to be rather easy, but I've never done it. I'm little hesitant since this is my only computer and I need it. Anyhow, your install should be fine, but not quite perfect out of the box. You'll need to tweek a couple of things. Good luck.

---

### Post by mmb1 on 2008-01-24
With enough RAM, that machine would run wonders with Ubuntu!  If that doesn't work out, you may want to run xubuntu or fluxbuntu.  Dig in, experimenting with hardware is always fun.

---

### Post by wolfear on 2008-01-25
> **sTpny said:**
> I have a Dell OptiPlex GX1 running with ubuntu on it. It runs just fine, but it doesn't install with sound or support for 3d graphics. For sound, you'll need to add the line snd-cs4236 to your /etc/modules file. The 3d graphics I haven't figured out yet, but I know others have gotten it to work.  It also boots gutsy gibbon saying that "the bios (1999) fails cutoff age (2000) acpi=force is required to enable acpi.", and I'm not quite sure yet where to put that. Without it, none of the computers advanced power saving features will work.  This was a little strange, since feisty faun had them all enabled after install. (it was actually the first time any operating system was able to put this computer to sleep. 

I'm thinking that rather than adding acpi=force, a better solution is flashing the bios with an update, which I see from our friends post is supposed to be rather easy, but I've never done it. I'm little hesitant since this is my only computer and I need it. Anyhow, your install should be fine, but not quite perfect out of the box. You'll need to tweek a couple of things. Good luck.

I don't know what could be up with your sound. I never had any sound issues using the onboard for any operating system on my GX1. If using a card, that's a different matter.
[EDIT] I did have a sound issue once. I turned it off in my Setup and forgot. Major "DOH!"

As for 3D, you can't get decent (if any) 3D from the onboard video. The only way to get 3D is with a card.

Do not worry about the cutoff age message. If your system boots and runs, it doesn't matter. It just means we are running dinosaurs. The GX1 doesn't really have any "advanced power features" in the sense that message is talking about.

Before you flash, make sure you actually need it.
 A BIOS flash is not to be entered into lightly even if it is relatively easy and if it goes bad (which can easily happen) you will probably have a paperweight as the BIOS chip on the GX1 setup is soldered (so you can't order a replacement unless you are really good at that sort of work).

On a sad note, my GX1 finally died. The PSU finally gave out after all these years.
On a happy note, it didn't take the mobo or anything else with it as is so often the case.
It just went to sleep on night and never woke up.

---

### Post by tgalati4 on 2008-01-25
I've got a GX1 with 768 MB of RAM, runs Linux Mint 4 XFCE just fine.  Problems with suspend under Mint 4/Gutsy.  SLED 10 works with suspend well on this machine.  Still troubleshooting it.  60-90 watts of power when in use, 33 watts in Suspend-to-RAM mode.  Good workhorse machine.

---

### Post by Paulmd on 2008-01-25
> **sTpny said:**
> I have a Dell OptiPlex GX1 running with ubuntu on it. It runs just fine, but it doesn't install with sound or support for 3d graphics. For sound, you'll need to add the line snd-cs4236 to your /etc/modules file. The 3d graphics I haven't figured out yet, but I know others have gotten it to work.  It also boots gutsy gibbon saying that "the bios (1999) fails cutoff age (2000) acpi=force is required to enable acpi.", and I'm not quite sure yet where to put that. Without it, none of the computers advanced power saving features will work.  This was a little strange, since feisty faun had them all enabled after install. (it was actually the first time any operating system was able to put this computer to sleep. 

I'm thinking that rather than adding acpi=force, a better solution is flashing the bios with an update, which I see from our friends post is supposed to be rather easy, but I've never done it. I'm little hesitant since this is my only computer and I need it. Anyhow, your install should be fine, but not quite perfect out of the box. You'll need to tweek a couple of things. Good luck.

A bios update will fix that acpi problem. As the last bios wos written in 2001, after the "cutoff date"

A dell is just about the easiest machine to do a bios update on, the catch is you need a windows machine to make the floppy disks.


[http://support.dell.com/support/downloads/driverslist.aspx?os=LNUX&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=PLX_PNT_PII_GX1&hidos=BIOSA&hidlang=en](http://support.dell.com/support/downloads/driverslist.aspx?os=LNUX&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=PLX_PNT_PII_GX1&hidos=BIOSA&hidlang=en)

---

### Post by wolfear on 2008-01-26
> **Paulmd said:**
> A bios update will fix that acpi problem. As the last bios wos written in 2001, after the "cutoff date"

A dell is just about the easiest machine to do a bios update on, the catch is you need a windows machine to make the floppy disks.


[http://support.dell.com/support/downloads/driverslist.aspx?os=LNUX&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=PLX_PNT_PII_GX1&hidos=BIOSA&hidlang=en](http://support.dell.com/support/downloads/driverslist.aspx?os=LNUX&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=PLX_PNT_PII_GX1&hidos=BIOSA&hidlang=en)

True, it is very easy to flash, but one shoud actaully be sure that what one is trying to fix is actually broken.
The BIOS updates after Rev A07 have been known to cause more problems than they fix.

Unless you need one of a few very specific fixes, any BOIS after Rev A07 is unnecessary and not recommended.

---

### Post by Paulmd on 2008-01-26
> **wolfear said:**
> True, it is very easy to flash, but one shoud actaully be sure that what one is trying to fix is actually broken.
The BIOS updates after Rev A07 have been known to cause more problems than they fix.

Unless you need one of a few very specific fixes, any BOIS after Rev A07 is unnecessary and not recommended.

Do you have a source on that, for this machine? I ask because I work on this generation of machines often enough.

But in any case, the op's problem is definitely fixable by a bios update. Essentially this: Gutsy is being stupid and is thinking any bios written before 1999 does not support acpi, which the GX1 does have. Updating the bios changes the revision date to 2001. Thus, problem solved. :)

---

### Post by Paulmd on 2008-01-27
> **wolfear said:**
> 
On a sad note, my GX1 finally died. The PSU finally gave out after all these years.
On a happy note, it didn't take the mobo or anything else with it as is so often the case.
It just went to sleep on night and never woke up.

Y'know, that's an easy fix. Grab the psu from another p2 or p3 class dell. They're all the same, until you get into the server/workstation line. And they don't have a high failure rate, even at the age your machine is. they pretty much keep going. Even though they're only 250 watts, if you have 3 or 4 hard drives, it doesn't matter, those psus are underrated, unlike most others. Dell sold millions and millions of these, spare parts are everywhere. You want one, i can ship you one. 


In my experience, the one machine where losing the psu is totally fatal is a black and silver emachine. Evil.

[COLOR="Red"]Edit: If you have an SFF machine (micro-desktop, has a laptop style cdrom), that one is special. I could still find one.[/COLOR]

---

### Post by wolfear on 2008-01-28
> Do you have a source on that, for this machine? I ask because I work on this generation of machines often enough.
I will check on the specific of the BIOS Rev information.
I printed out a list a long time ago but will have to dig through my file cabinets to find it.
One thing I do remember is that BIOS after Rev07 don't work with certain CPU's, but do not remember which ones off hand.

> Grab the psu from another p2 or p3 class dell. They're all the same, until you get into the server/workstation line.
I have a ton of (good) PSU laying around. I just haven't had the time to put a new one back into my GX1.

> **Paulmd said:**
> 
In my experience, the one machine where losing the psu is totally fatal is a black and silver emachine. Evil.

I totaly agree about the emachine. I have a dead one sitting under my workbench right now.

[Update] I stand corrected: RIght after I posted this I was reading the Dell website and Rev A09 may be a fix for the date and the ACPI issue.
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R18383&SystemID=PLX_PNT_PII_GX1&servicetag=&os=BIOSA&osl=en&deviceid=162&devlib=0&typecnt=0&vercnt=6&catid=&impid=&formatcnt=2&libid=0&fileid=18126]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R18383&SystemID=PLX_PNT_PII_GX1&servicetag=&os=BIOSA&osl=en&deviceid=162&devlib=0&typecnt=0&vercnt=6&catid=&impid=&formatcnt=2&libid=0&fileid=18126")

---

### Post by Paulmd on 2008-01-28
> **wolfear said:**
> I will check on the specific of the BIOS Rev information.
I printed out a list a long time ago but will have to dig through my file cabinets to find it.
One thing I do remember is that BIOS after Rev07 don't work with certain CPU's, but do not remember which ones off hand.


I have a ton of (good) PSU laying around. I just haven't had the time to put a new one back into my GX1.


Just so long as you remember that that generation of dell is NOT a standard atx. It's an atx-looking plug, but it's not. :)  Most of the p4 class and later Dells are standard atx now. (Not the dimension 8100, which is even more proprietary )

PS:* Every* tech has a dead emachine under their bench, or will soon. They're that reliable. :)

---

### Post by ilikepants on 2008-01-29
> **wolfear said:**
> 
[Update] I stand corrected: RIght after I posted this I was reading the Dell website and Rev A09 may be a fix for the date and the ACPI issue.
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R18383&SystemID=PLX_PNT_PII_GX1&servicetag=&os=BIOSA&osl=en&deviceid=162&devlib=0&typecnt=0&vercnt=6&catid=&impid=&formatcnt=2&libid=0&fileid=18126]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R18383&SystemID=PLX_PNT_PII_GX1&servicetag=&os=BIOSA&osl=en&deviceid=162&devlib=0&typecnt=0&vercnt=6&catid=&impid=&formatcnt=2&libid=0&fileid=18126")

Is there any reason you chose to use Rev A09 and not A10? I ask because using A10 causes all sorts of interesting ACPI errors. 

Also this is slightly off topic, sorry to thread steal, but has anyone got the thermal monitors via ACPI or lm-sensors to work for the optiplex gx1? 

I got it to work in 6.06, but I can't remember what it was I had to do. Lm-sensors says that there are no sensors, even though sensors exist. The sensors are listed as a supported chip for lm-sensors. I believe the problem is due to Dell disabling the chip. I know there is a module that has to be loaded first and then there is a script that will work, but can't remember what it was :(

---

### Post by ilikepants on 2008-01-30
Nevermind on the temperature, I remember the module which is dcdbas. This led me to SMBios which includes a utility to monitor the temperature, though it is only a POC.

I'd still like to know if there was a reason you choose Rev A09 over A10 though.

Thanks

---

### Post by Paulmd on 2008-01-30
> **ilikepants said:**
> Nevermind on the temperature, I remember the module which is dcdbas. This led me to SMBios which includes a utility to monitor the temperature, though it is only a POC.

I'd still like to know if there was a reason you choose Rev A09 over A10 though.

Thanks


Did you say a10 causes weird acpi errors? If so that would be reason enough to use a09. If you meant to say a09 causes weird acpi errors, then it's reason enough to use a10.

---

### Post by wolfear on 2008-01-30
> **ilikepants said:**
> 
I'd still like to know if there was a reason you choose Rev A09 over A10 though.
Thanks
Rev A09 addressed the ACPI and date issue. 
A10 is A09 with added support for Cisco Routers.
Unless one needs a Cisco interface, A09 should work just fine.

---

### Post by sTpny on 2008-03-10
Quick update guys, I added acpi=force to my /boot/grub/menu.lst and now all my power saving functions work again. I put it just before where it say root=UUID-etc, and everything works just as it should, so I won't bother with the bios update.  

On the subject of 3d graphics, I had them working for a while, but then I let my system update my xserver-video and then my settings were wrong and I had to dpkg-reconfigure xserver-xorg before I could get any graphics to work again. Now, no 3d again. Back to the drawing board. 

Anyone else have any luck with getting 3d out of their GX1?

---

### Post by scottjetton on 2008-04-26
> **totalnub said:**
> well, i need you guys to give me some feedback on whether or not ubuntu/xubuntu would work on this machine. [http://docs.us.dell.com/support/edocs/systems/ban_gx1/specs.htm](http://docs.us.dell.com/support/edocs/systems/ban_gx1/specs.htm)
i found one with no ram or hdd. i am wondering if anyone has tried this type of machine and whether or not booting from a cd works......any help is appreciated.
the answer is yes. AM running the dell optilplex gx1 and am running ubuntu. the only thing is the sound doesn't work but i do have over 400mb of ram and the processor is . 333m  ~Tech Man~

---

### Post by wolfear on 2008-04-28
The new release (8.04) has given me initiative to start putting my GX1 back together as time permits, as I am curious how it will work.
Hopefully, I will have it up and running by the weekend.
Maybe by the first of next week, I'll be able to post back with the results.

---

### Post by mtb_kng on 2008-06-04
hey i have the same computer and i had the acpi=force problem but i updated bios and that fixed it but now i just get a black screen where the error came up and then the dvd/cd drive slows down?
help requested?

---

### Post by Taollan on 2008-06-04
Hey, I have just got my hands on a GX1p and wanted to put linux on it.  Unfortunately, I can seem to get it to boot from cd.  I have specified CD first boot from the bios, and it looks for a moment or two at the CD, but then boots from HD.  It appears the be running the standard CDRom, and the CD is bootable on other computers.  Anyone have any thoughts?

---

