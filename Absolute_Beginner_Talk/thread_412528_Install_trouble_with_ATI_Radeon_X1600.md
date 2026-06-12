---
title: "Install trouble with ATI Radeon X1600"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by onlyteo on 2007-04-18
I want to install Ubuntu Desktop for the first time on my Acer TM8215 where i am already running Win XP. My laptop has the ATI Radeon X1600 graphic card, and from reading a bunch of forum threads i have understood that this can be a bit troublesome.

Many threads deal with editing the xorg.conf or other settings, but all i have found handles troubleshooting after the OS is installed.

I cant even get that far. After selecting "Start or install Ubuntu" in the startup dialog it loads the ramdrive. But when the installer tries to load the system the screen becomes a blur. This has to do with my graphic card driver im assuming.

Can i install without loading the system first, if so; what is the install command to use in the startup dialog?
Or is the another way that is easier?

---

### Post by aberry5555 on 2007-04-18
Follow this link and it will help you through it, I had this problem with my X800, it seems its the "ati" driver that's broken :S

[https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)

The only think I would do differently in that walkthrough is, instead of using the "vesa" drivers as it says to, try the "radeon" drivers as they're the proper open-source ones.

Good luck :)

**EDIT**

Also, you probably already know this, but if you don't Linux is COMPLETELY case-sensitive, so make sure you type in "vesa" or "radeon" rather than "VESA", "Vesa", "RADEON" or "Radeon".

---

### Post by onlyteo on 2007-04-18
Thx for humoring me, but i am a total newbie on linux. But that was what i was going to change, atleast that was my hope. :) 

The xorg.conf file said 'vesa' and 'ATI Technologies, Inc. default graphic card'. So it seems that the system didnt identify my graphic card fully. I tried with 'radeon', but got an error. Could it be that i have a 15.4'' Widescreen monitor on my laptop? In the monitor setting only 1680x1050 resolutions were listed.

---

### Post by lamalex on 2007-04-18
yeah you could try changing that res down to 1200x800 or something suitable, that might help you.

---

### Post by onlyteo on 2007-04-18
That didnt help either. Tried to change from 'vesa' to 'ati' too, but no go. :confused: This is exactly why newbies doesnt change to Linux. I consider myself a quite skilled computer user, above average at least. But things like this really deter me from trying Linux, and i really want to.

Can it be that the Ubuntu Live-CD doesnt have the correct ATI drivers? I have just downloaded the latest image from ubuntu.com, ver. 6.10. Im about to give up :(

---

### Post by mcduck on 2007-04-18
With X1600 you'll want Ati's own fglrx drivers:

```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
```

you may also need to add following section to the end of xorg.conf:
```
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

(and yes, that driver does not come with Ubuntu, as it's not free)

---

### Post by onlyteo on 2007-04-20
So is there any way to install that driver so i can start the Ubuntu ram-drive in order to install Ubuntu? I see that there are heaps of people that have written about similar problems with their ATI and GForce cards. Someone must have found a solution to this problem? My xorg.conf file uses the 'vesa' setting, so why wont that work?

---

### Post by onlyteo on 2007-04-21
Downloaded the latest disto, Ubuntu 7.04. Could start and install that, no prob. Thanks for all your advice.

---

