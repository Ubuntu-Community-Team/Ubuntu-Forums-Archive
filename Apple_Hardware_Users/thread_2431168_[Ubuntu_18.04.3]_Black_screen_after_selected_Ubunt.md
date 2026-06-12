---
title: "[Ubuntu 18.04.3] Black screen after selected Ubuntu in GRUB."
date: 2019-11-12
forum: Apple Hardware Users
---

### Post by henry00carlsson on 2019-11-12
Hey! So i just installed Ubuntu 18.04.3 on my MacBook Pro 13 (mid 2010). I have had some problems with the neuveau grahics drivers, and i think it's one of many problems here. Anyways, after installation i rebooted my mac as told, and startup sequence were going great, until it hanged on something like: 

[   ok   ] Starting hold until boot sequence finises up...
or
[   ok   ] Started WPA supplicant
or some other UID 7... something.

I fixed my original harddrive space problem i had here earlier, so i'm going to remove that one. Anyways, now, everything is installed, (rEFInd bootmanager) aswell. BUT!!

When booting from the EFI partition belonging to ubuntu, and booting into GRUB, i just get a purple screen. After about 10 - 20 seconds, 
a black box appears in the middle, and a few graphical glitches aswell. Then all of the "[  ok  ]s" starts appearing. And after another 5-20 seconds, the mac
is stuck on one of many different [   ok   ] checks, and just flashes.

===UPDATE!===
 As it turned out, i could access GRUB with a simple ESC press during the purple screen. I entered it, wrote "nomodeset" after quiet splash, and voila! Ubuntu booted.
After i changed the grahics driver from "nouveau" which only causes problems, to nvidias proprietary and rebooted i once again entered "nomodeset". However, now the screen dies after the purple
screen. It doesn't just turn black, it just shuts off completely. The mac is still running, fans and harddrive is making normal sounds, but screen is off and it doesn't respond to any input.

All help with this problem is appreciated :) macOS High Sierra is old software now a days, it's time for Ubuntu to take over :)

(Note that i've dual-booted macOS High Sierra with Ubuntu 18.04.3 WITH rEFInd bootmanager)

---

### Post by Frogs Hair on 2019-11-12
Moved to ***Apple Hardware Users***.

---

### Post by oldfred on 2019-11-12
Do not know Mac.
Often issue is runaway log file(s).
Unless you downloaded a lot of videos or other large files.

cd / or cd /home
sudo du -hc --max-depth=1
Shows just [COLOR=#ff0000]/[/COLOR]
sudo du -hx --max-depth=1 [COLOR=#ff0000]/[/COLOR] 2> /dev/null

Then you can drill down in / to /var or whatever folder is large and run command again
sudo du -hx --max-depth=1 [COLOR=#ff0000]/var[/COLOR] 2> /dev/null
Or just top 10 in order:
sudo du -a /var | sort -n -r | head -n 10

---

