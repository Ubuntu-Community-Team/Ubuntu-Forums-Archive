---
title: "Trying to install ubuntu.."
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Tinnian on 2006-09-28
O.K., so here is what I am dealing with, and I am BEGGING for an idea on what to do.

I received my Ubuntu from Shipit 4 days ago and when I tried just to run the live cd, it hangs. I get 2 notes while it's running the install:



pcmcia: not present

manual drivers : mount function not implemented 

Everything else says "ok".

It continues to load until I get the window manager ( Start up), then it just stops on this screen and does nothing. Literally, I have no mouse nor keyboard, and the last time I tried to load it, it shut down the computer. When it restarted all I had in the bios was the floppy. No hard-drive or cd drive was "seen". Got past that, but I am wondering if I am doing something wrong here. 

It has now been running for ten minutes and while the cd is still spinning like a madman in the tray, all I have is a plain brown screen. 

I have heard nothing but good about Ubuntu and I really would like to try this out for myself. 


Oh yeah... it is an old Dell (yeah, I know) Optiplex gx110, 733mhz, stock hardware, no os, if that helps any

---

### Post by gn2 on 2006-09-28
Have you tried the different boot options, I think it's F6, they're on the bottom of the screen. Perhaps try "noapic nolapic"

If it's a help, I can confirm that an Optiplex GX110 SFF works OK with Ubuntu, just needed to up the RAM to 256mb.

---

### Post by rahelvey on 2006-09-28
On this old box I used the older system install and everything works like a champ.
Oh I also used automatix.

---

### Post by Jareth on 2006-09-28
hi, don't know if its the same issue but the disc always hangs for me unless I add aload of nonsense to the boot option,

press f6 and straight after whats in there already, I add:

gdth=disable:y mca-pentium nohlt acpi=off noapic nolapic

mine works with that, I have a feeling you might need to change the bit about pentium if you dont use a pentium. Maybe try it without the 'mca-pentium' bit.

If its any use I'm sure other folk will edit it for your needs.

---

### Post by uk_sphinx on 2006-09-28
i installed from downloading it from the net and burning a copy to disc.
i never had 1 prob so far.
dont know wether or not it is a safer bet for you or not.
youl need a cdr of course

---

### Post by djheadley on 2006-09-29
You might have just gotten a bad cd, it happens sometimes.  Can you try it in another machine?

---

### Post by LAA1010 on 2006-10-03
Hi all, new here and not sure if this is the right place for all this detail, but my problem fits with this thread.

Tinnian, it sounds like we have a very similar (perhaps same) problem. I boot the install cd and get to the standard start screen (where you can start, start in safe graphics mode, or run memtest).

If I run the regular start, the whole thing locks up as you described after trying to start the gnome display manager (except my cd completely stops spinning and the whole thing grinds to a halt).
If I run the safe graphics mode, it will fail to start the Xserver and the Alt-F2 console turns to absolute garbage (tough to describe better than that). However, the consoles on Alt-F1,F3-F7 look like normal ubuntu$: prompts and Alt-F8 is the console displaying all the information ubuntu is trying to load/start/etc...
I also tried running with the boot options listed by Jareth, but they had no effect.

This box in particular is an optiplex gx110, pentium 3 866 MHz, with 512MB of ram. One problem is that the onboard video chip does not work and I am using an nVidia card for my display, but there is no way for me to disable the onboard video support in Bios A05. Consequently, the xorg.conf file in /etc/X11/ is defaulted to use the onboard chip instead of the card (have not been able to successfully change that).
You may have a similar problem with X configuration.

Can any of the more experienced folks on this forum tell me how to get su access (i.e. I don't know the root password at the ubuntu$ prompt I can get to from safe graphics mode) so I can change permissions on xorg.conf and change the display information?

Here is the lspci output from my machine if it's useful to anyone.
-------------------
0000:00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE bridge: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
0000:01:07.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
0000:01:0c.0 Ehternet controller: 3Com Corporation 3c905c-TX/TX-M [Tornado] (rev 78)
----------------------

Thanks.

---

### Post by CatKiller on 2006-10-03
> **LAA1010 said:**
> Can any of the more experienced folks on this forum tell me how to get su access (i.e. I don't know the root password at the ubuntu$ prompt I can get to from safe graphics mode) so I can change permissions on xorg.conf and change the display information?


```
sudo -s
``` or ```
sudo -i
```

---

### Post by Tinnian on 2006-10-04
Well, as it turns out, I was trying to load using some of the suggestions that I had heard about and now when I try to boot the computer; it tells me that hdd and cdr are not installed (bios) and won't even try to boot. Tried reseting bios to factory, no dice, tried loading an old w98 boot floppy, no dice again.:-? 

Guess I am going to have to rebuild this thing. (Oh well, I got the box for $10 from a neighbor who said it was "too old" :D  )

---

### Post by Dragineez on 2007-02-06
I had the same problem. Boot installation parameters that got it to recognize the CD:

```
boot: install ide=nodma pci=noacpi acpi=off aic7xxx=noprobe noapic nolapic hw-detect/start-pcmcia=false
```

---

### Post by lyceum on 2007-02-06
> **Tinnian said:**
> Well, as it turns out, I was trying to load using some of the suggestions that I had heard about and now when I try to boot the computer; it tells me that hdd and cdr are not installed (bios) and won't even try to boot. Tried reseting bios to factory, no dice, tried loading an old w98 boot floppy, no dice again.:-? 

Guess I am going to have to rebuild this thing. (Oh well, I got the box for $10 from a neighbor who said it was "too old" :D  )

Try Fluxbuntu:

[http://fluxbuntu.org/](http://fluxbuntu.org/)

light and fun. But you would have to have a friend download it and burn it for you. No ship it cd's :(

---

