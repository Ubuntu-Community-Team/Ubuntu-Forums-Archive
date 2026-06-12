---
title: "PPC - Intrepid 8.10 on G5 iMac 20&quot; success"
date: 2008-11-08
forum: Apple Hardware Users
---

### Post by stream303 on 2008-11-08
Just got Intrepid up and running on my G5 iMac 20" (rev-a) with Ubuntu Intrepid 8.10.  It's a keeper.  Fortunately, this model of iMac doesn't present too many problems.  I used the "alternate" Ubuntu image for Intrepid.  (server worked too as a test!)

Thanks to the community, you guys got me started out of the gate by having to use

```
modprobe ide-scsi
```

in a virtual terminal (ctrl-alt-f2) to get it to detect my cdrom.  I just went back a step and installation went fine.

Like all other Ubuntu installs, the fans will run at full speed, but with cool air, until after the first reboot and then it calms down.

The screen stays black until the gui comes up, so I just use "nosplash" on either the 2nd-stage boot prompt, or I just put it into my /etc/yaboot.conf file (with a subsequent ybin -v -C /etc/yaboot.conf) to make the change permanent.  Maybe I'll play with usplash later, but for now I don't mind seeing the boot messages scroll by at startup.

Like Hardy, the screen has a small amount of right-side wrap-around, about a quarter of an inch, and this problem is coming upstream from freedesktop.org, and has been reported.  No known fix to date, as this was a regression to fix someone else's issue not ppc related with the nv driver.  Fortunately, there's enough screen real-estate for this to be a minor annoyance - at least to me.  Might be a deal-breaker for some.

Since I'm running 1680x1050 screen resolution, I make sure to set my dpi to 100, in the appearances setup, rather than the default 96, and the fonts, especially the small ones, look very good.  I also set up for subpixel smoothing for lcd.

Normally I like to turn on dithering for my nvidia card, and have to do that manually in xorg.conf, but with Intrepid, xorg.conf contains nothing, and my attempts to put something in there results in going to an unreadable low-graphics mode.  I'll have to do more research on that later because I like to enable "Option FPDither True" on any system using the nv driver, be it intel/ppc, from any manufacturer.  I used to do a lot of xorg.conf editing, but this blows me away. :)

For the PPC repositories, I went into the "third party" tabs, and unchecked all the source-code repos.  No need for them for me, and the system updates faster.

CPU frequency scaling works with the edit to the powernowd file as shown in the faq, but if I wanted a bit snappier system, I'd stick to my usual trick of replacing powernowd with cpudyn - especially for audio / video editing.  Thanks again to the community for posting that powernowd fix.

The audio slider issue seems to be fixed that popped up in Hardy, so I'm very pleased - even with the default pulseaudio running.  Nice not to have to do anything there.

Overall, I'm very pleased with Intrepid on this box, and once again I'm impressed with the response from the ppc community for coming to each other's aid.

Update - Nov 10.  Screen brightness: Although not super bad, the screen is a tad bright.  Intrepid has a nice built-in theme called "DarkRoom" that really helps.  I suppose one could do it themselves, but this was pretty handy.


Thanks again...

---

### Post by cyberdork33 on 2008-11-08
Hey stream,

just for fun, could you give me the output of
```
sudo dmidecode -s system-product-name
```
for that machine. I am guessing it should be "iMac3,1"

---

### Post by stream303 on 2008-11-09
Well, there doesn't seem to be any dmidecode on the ppc release, however, here is the output of my

cat /proc/cpuinfo:

```
processor	: 0
cpu		: PPC970FX, altivec supported
clock		: 900.000000MHz
revision	: 3.0 (pvr 003c 0300)
timebase	: 33333333
platform	: PowerMac
machine		: PowerMac8,1
motherboard	: PowerMac8,1 MacRISC4 Power Macintosh 
detected as	: 338 (iMac G5)
pmac flags	: 00000000
L2 cache	: 512K unified
pmac-generation	: NewWorld
```

System is rated at 1.8ghz, but when the cat was taken the system was idling at 900mhz..

---

### Post by cyberdork33 on 2008-11-09
that is interesting:
PowerMac8,1

I wouldn't have suspected that. I wonder what happened to the other iMacX,X versions...

Thanks though!

---

### Post by stream303 on 2008-11-09
My pleasure.  That's one thing I really like about

[http://www.everymac.com/](http://www.everymac.com/)

They list all the Gestalt/Model Id's in their specs for each model, and also some variations that might show up like education-only models that had limited runs, etc...

---

### Post by cyberdork33 on 2008-11-09
> **stream303 said:**
> My pleasure.  That's one thing I really like about

[http://www.everymac.com/](http://www.everymac.com/)

They list all the Gestalt/Model Id's in their specs for each model, and also some variations that might show up like education-only models that had limited runs, etc...
Awesome we were just looking at this information today.

mactracker is also a good one:
[http://mactracker.dreamhosters.com/](http://mactracker.dreamhosters.com/)

---

