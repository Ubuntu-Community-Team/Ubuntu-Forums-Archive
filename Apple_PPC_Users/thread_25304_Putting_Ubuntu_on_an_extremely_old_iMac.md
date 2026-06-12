---
title: "Putting Ubuntu on an extremely old iMac"
date: 2005-04-09
forum: Apple PPC Users
---

### Post by timelord726 on 2005-04-09
Hi everyone!  I have two extremely old Macs that are just sitting and gathering dust.  One of them is an extremely old iMac.  It's definitely a G3 from a good seven or eight years ago, before they introduced the different colors and the newer push-in CD-ROM drives, but I'm not sure of the exact model.  Is it possible to put Ubuntu on this old clunker?

While I'm at it, and going back another few years, I have an even older Power Macintosh 5500/225.  What are the chances of putting Ubuntu on this thing?

Thanks in advance for your assistance!

---

### Post by humanity_to_others on 2005-04-09
InstallOnOldWorldMacs: [http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)

---

### Post by Rxke on 2005-04-10
iMac should be no problem using the default ISO. It's a newworld Mac

---

### Post by pvz on 2005-04-10
It works great on an iMac. I have the first model, revision A 233MHz iMac first generation with 96 mb memory, and it serves as my jukebox, with a 80 GB disk running Kubuntu and Amarok. It's a single task machine for me, maybe a bit too slow for normal daily use. But yes, it works. Just pop in the install CD and you're ready to go.

---

### Post by Len on 2005-04-10
It will be more then quick enough for daily use if you put in some more RAM. Gnome doesn't like 96 MB, actually it requires 256 MB or more.

You can build IceWM from source, it works on the PowerPC. I did this for my 5500/275 and that one runs fast now, apps like the Gimp and FireFox fly. Maybe that's also because I upgraded the 275 MHz 603 to a 233 MHz G3 processor ;-).

---

### Post by timelord726 on 2005-04-10
[QUOTE=pvz]It works great on an iMac. Just pop in the install CD and you're ready to go.[/QUOTE]
Pop in the install CD and then what?  I have my iMac upgraded to an early version of OS X.  Assuming I've booted into that, exactly what do I need to do to get it to run?  (I don't mind losing everything on that machine.)

---

### Post by Rxke on 2005-04-10
With the disk in the iMac, reboot it holding the c button, so it starts up from the disk.

If you have internet, it might be interesting to have your iMac connected, since networksetup can be done in one go and some stuff can get updated that way.

---

### Post by timelord726 on 2005-04-11
[QUOTE=Rxke]With the disk in the iMac, reboot it holding the c button, so it starts up from the disk.[/QUOTE]
I'm afraid that didn't work. Holding "C" on startup with the install disk in the drive does nothing. I get the happy Mac, the spinning color wheel, then Mac OS X starts right now.

---

### Post by Rxke on 2005-04-12
Hmmm... How did you aquire the ISO?

Looks like your iMac doesn't recognize it, which it should... So there's probably something wrong with that disk.
If you burned it under osx, there's an issue with Panther, which doesn't like to burn Ubunto for some reason, I used the free MissingMediaBurner, which did the job for me, after some fiddling.
Or... did you try starting up with the default os9 or osx cd? Does that work? If not, it could be your cd reader, having been unused for all that time or something like that....

---

### Post by timelord726 on 2005-04-12
Well, the ISO was acquired on my PC and burned from Windows.  Would that make a difference?  I'll try again later today and make sure I'm not doing something stupid.  Thanks!  I'll get back to you.

---

### Post by Len on 2005-04-12
The old trayloading CD iMacs had a not-so-good quality CD-ROM player.

Use TDK Reflex, Verbatim or Sony CDs (or any other brand you know is good, NOT arita, octron or that kind of crap), and burn the CD at 1x, 2x or 4x speed.

Most cheap CD writers produce errors when burning on max speed, not to mention producing discs almost unreadable just under the maximum.

Did the CD actually appear on the desktop when the Mac OS was booted?

---

### Post by timelord726 on 2005-04-12
[QUOTE=timelord726]I'll try again later today and make sure I'm not doing something stupid.[/QUOTE]
I guess trying to install Ubuntu off the x86 install disc would be one of those stupid things I was trying to avoid, eh?  :?

Got the installer running exactly as it should be this morning once I finally realized I needed the PowerPC disc. Give me a break, though -- it's my first time doing anything Linux-related on a Mac. :-#

---

### Post by Rxke on 2005-04-12
[QUOTE=timelord726]I guess trying to install Ubuntu off the x86 install disc would be one of those stupid things I was trying to avoid, eh?  :?

Got the installer running exactly as it should be this morning once I finally realized I needed the PowerPC disc. Give me a break, though -- it's my first time doing anything Linux-related on a Mac. :-#[/QUOTE]
 trying desperately not to grin ;)

Well, end good all good.

---

### Post by Len on 2005-04-12
Hehe... and I was thinking about a bad quality CD :P.

How much RAM does that 5500 have? If it has less as 64 MB of RAM you'd better upgrade it or put an old Mac OS on it. There are 10.000's of apps available for that old system, but no FireFox, which is exactly the reason I installed Ubuntu.
If you need any help with BootX just ask.

BTW: nice avatar, Rxke!

---

### Post by Rxke on 2005-04-12
re: the Avatar: i found it in an article on a Belgian mag, and couldn't resist shamelessly recycling it...

About the minimum 64Mb... Is that so?
I've got an 8500 with 48Mb, and was thinking about Ubuntuiziing it, one of these days...

---

### Post by Len on 2005-04-12
[quote="Rxke"]re: the Avatar: i found it in an article on a Belgian mag, and couldn't resist shamelessly recycling it...[/quote]
I wish they would put such stuff in Dutch magazines :P. I think FireFox is even better as Apple's Safari.

[quote="Rxke"]About the minimum 64Mb... Is that so?
I've got an 8500 with 48Mb, and was thinking about Ubuntuiziing it, one of these days...[/quote]
According to Top Ubuntu with IceWM takes up 60 MB. When I started FireFox the page-outs start to raise. I've put in an additional 32 MB, totalling it to 96 and now FireFox doesn't cause page outs, and OpenOffice is suddenly usable. So yes, I think 48 MB is a bit too little. You can always try to fully customize the system by leaving out a lot of packages, but still... Gentoo *might* be a good choice for those machines. You can let your fast G4/G5 help compile, so you won't be compiling days :).

---

### Post by Rxke on 2005-04-12
]
 My fast g4-g5... Sigh. I wish... The 466 MHz iBook is the fastest computer I have, my desktop is a g3@350MHz...

Sometimes that's frustrating, but then I recall the 8-bit days, and I stop grumbling.

---

### Post by Len on 2005-04-12
[quote="Rxke"] My fast g4-g5... Sigh. I wish... The 466 MHz iBook is the fastest computer I have, my desktop is a g3@350MHz...

Sometimes that's frustrating, but then I recall the 8-bit days, and I stop grumbling.[/quote]

Sorry

I upgraded from an iMac DV 400 to a G4 1.25 GHz a year ago. It was cheap since the G5 was just in stores. I sold my DV for about $500, my older iMac G3 for $250, and bought that G4 for $1100. Now it will still take some years until I can afford/have need for a G5 (probably when the G6 or G7 is shipping :). Try to sell and buy at the good moments. The Mac Mini for example is already being sold secondhand for $450, mostly because they purchased one too much or bought a G5 because of 'full confidence'. The 1.45 GHz mini is faster as my G4 in processor power; I tested it; they didn't cripple it.

However, two G3s + an 8500 must come near the speed of that G4 of mine (thinking of linking them all up to let them all participate in the compilation process), and a 466 MHz iBook is still perfect for Mac OS X or Ubuntu, as long as it has the RAM needed.
My sister is still working on an iMac 266 (rev C) with 288 MB RAM. She uses OS X 10.3.8 and a lot of applications, no complains (except about "no videochat in MSN for the mac! Damn MS...).

And about those 8 bit machines, well, I never got one, but I still have my "dirty" 32 bit SE/30 with System 7 on my desk. Love the machine, the system and the software. Almost as functional as my new machines (well, you know what I mean) and the system takes 1 MB RAM, MS Word, Excel and Powerpoint 500 kb, the web browser 2 MB (iCab) and everything is quick. Sure, a 9" screen with 2 colors isn't that good for photoshop and illustrator, but those also run fast with minimal memory. Don't expect such things to be cross-platform though, all assembly :)

---

### Post by Rxke on 2005-04-13
Yes, I know... should've upgraded ages ago.
Then again... what for? When I bought my machine it was the fastest one in the neighbourhood, we used it to edit video, which was still pretty cumbersome (despite the blazingly fast G3@350MHz and the rediculously big amount of 300+ Mb, heh.)
The machine is still good enough at what I'm doing with it today.

Anyway, I clocked my boottime.
it's longer than booting OSX, I have the impression.
... 2.49''
There are some things that should be substracted, though, 
20 secs of yaboot timouts (twice 10 secs)
The synchronisation with ubuntu time server takes IMHO too long, another 20 secs,
I set up XFCE to load both KDE and Gnome services, say another 10 secs.

So say Boot time is 2 minutes  :smile:  Better than my friend's new XPbox, heehee

---

