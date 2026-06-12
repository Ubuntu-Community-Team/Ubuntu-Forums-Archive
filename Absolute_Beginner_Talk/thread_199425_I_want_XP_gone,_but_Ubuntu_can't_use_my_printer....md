---
title: "I want XP gone, but Ubuntu can't use my printer..."
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by nealklomp on 2006-06-18
This is actually a request for suggestions--my first one in 6 months of Ubuntu usage.

I have an older desktop running XP, while my newer laptop which is by far my prime box runs Ubuntu with Gnome/Xfce GUI (starting to really dig X).
And it is good, I'm happy, except when I must have extended contact with the Desktop. It dogs, and is all windowsy.
What can I do?
The printer is that all-in-one dell 922 that is also a lexmark, yada yada, I've hunted for Linux drivers to no avail.
So I'm stuck with the Windows desktop.

_**I'm asking**_, *is there a way to run the windows application/driver (it is more than a program, but an actual app that controls the scanner also) with Ubuntu? Like, via WINE or NDIS wrapped?*

I would really like to erradicate microsoft from **MY** world.

---

### Post by aysiu on 2006-06-18
Lexmarks are notoriously difficult for Linux. Since you say you've already "hunted for Linux drivers to no avail," I'm going to say, "Give up... for now."

The truth is that you need to print, and you have a printer. Stay with Windows until your printer breaks or gets too old. Then, when you buy a new printer, find one that works with Ubuntu: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

If you're really that hurting to move over, consider selling your printer now and replacing it with a more Ubuntu-friendly one. Just tell all your friends and family, "It's a perfectly fine printer. I just need to buy one that's compatible with my new operating system."

---

### Post by nalmeth on 2006-06-18
Before you give up, I would advise you to try the PClinuxOS liveCD. 

Couldn't get a Lexmark printer setup in Ubuntu, but PClinuxOS set it up upon boot to KDE.

But if you can, totally ditch the lexmark and support a company that support's linux. :D

---

### Post by MetalMusicAddict on 2006-06-18
I had this same problem 6 months ago, but with a Canon. I bought a HP Photosmart 8450. Works like a charm.

---

### Post by nealklomp on 2006-06-18
[QUOTE=aysiu]Lexmarks are notoriously difficult for Linux. Since you say you've already "hunted for Linux drivers to no avail," I'm going to say, "Give up... for now."

The truth is that you need to print, and you have a printer. Stay with Windows until your printer breaks or gets too old. Then, when you buy a new printer, find one that works with Ubuntu: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

If you're really that hurting to move over, consider selling your printer now and replacing it with a more Ubuntu-friendly one. Just tell all your friends and family, "It's a perfectly fine printer. I just need to buy one that's compatible with my new operating system."[/QUOTE]
Yeah, I thought as much. That is why I asked, to see if I'd missed something, and I will try PClinuxOS nalmeth, thank you.

I could buy a new printer, but then this one is just a waste, and its about the principle, it isn't even a year old; and I need the all in one capacity as my space is limited so the 8450 won't work MMA (by the way loved the sticker thread, still haven't got off my duff and got one though, but I will).

Thanks again.

---

### Post by aysiu on 2006-06-18
By the way, PCLinuxOS is an all-around good distro to have around. I would never install it to my hard drive--as I much prefer Ubuntu, and PCLinuxOS doesn't detect my USB mouse or my sound card--but it is a much better wow-your-friends live CD than Ubuntu's live CD, and it includes proprietary codecs by default.

More importantly, it has the best partitioning program I've seen: DiskDrake.

---

### Post by Anduu on 2006-06-18
Have you tried this How-To yet?

[http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer](http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer)

Honest to god I thought all hope was lost then I tried it.Worked like a hot damn for my Lexmark 1185

---

### Post by nealklomp on 2006-06-19
Yeah, I saw that, it doesn't really address the issues with the All In One printer. Its more than just a driver, but a complete app because it controls printing, scanning, etc.
the Dell 922 is the like the lexmark x5840...
I did try Wine by the way, no go.
Thanks for the replies

---

### Post by %hMa@?b&lt;C on 2006-06-19
Ubuntu has support for hps very good.  Ditch that Lexmark.

---

### Post by Anduu on 2006-06-19
[QUOTE=nealklomp]Yeah, I saw that, it doesn't really address the issues with the All In One printer. Its more than just a driver, but a complete app because it controls printing, scanning, etc.
the Dell 922 is the like the lexmark x5840...
I did try Wine by the way, no go.
Thanks for the replies[/QUOTE]

The Lexmark 1185 is an all in one as well and no you can't control your scanner with it;however there are a few apps that can...XSane for example which works fine with my scanner.

---

### Post by ProjectGod on 2006-06-19
speaking of lexmarks... they wont even work properly on my windows machines... do they suck or what?

---

### Post by Griff on 2006-06-19
[QUOTE=ProjectGod]speaking of lexmarks... they wont even work properly on my windows machines... do they suck or what?[/QUOTE]
I've always bought lexmarks (they uber cheap just like I like) and I've never had any problems using all their functions...until I switched to Linux about a year ago.  My windows partition still lingers because of that printer.  :(

---

### Post by Anduu on 2006-06-19
Yup its sad to say their support for linux sucks but they do make a good printer.A shame really.

---

### Post by K.Mandla on 2006-06-19
Hmm. My Lexmark E232 works like a champ under Ubuntu. I use the Optra E321 driver and it's a cinch to set up. 

I guess it depends on the model. :|

---

### Post by ProjectGod on 2006-06-22
holy smoke! that's the exact lexmark model i use. 

cheers for that.:-D

---

### Post by ProjectGod on 2006-07-01
found a nifty little site [http://www.linuxprinting.org/](http://www.linuxprinting.org/) 

found ppd drivers for lexmark e321... selected network printer ... "samba host"... installed ppd driver downloaded from the above url... 

the printer is local to an xp home machine couldnt print to it from my win 2k machine... now i can print remotely using ubuntu! how choc a block grand is that?

---

### Post by Lord Illidan on 2006-07-01
If you want an all in one printer, I can recommend HPs PSC series. Printer Scanner Copier.

I have a PSC 1110, and while it is nearing the end of its service (rollers wearing out and all that), it is 100% functional in Ubuntu, scanner, and printer both included. And its pretty cheap too.

---

