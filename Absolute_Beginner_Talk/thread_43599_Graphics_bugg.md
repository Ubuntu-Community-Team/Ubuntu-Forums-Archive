---
title: "Graphics bugg"
date: 2005-06-22
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-22
Why are windows "lagging" like this when I move them? I use a GeForce4 Ti4200 with the nv-drivers. nv is for nVidia cards, right? And nVidia for newer nVidia cards or something?

nv was tha autochoosen drivers for my card.

[http://upl.silentwhisper.net/uplfolders/upload2/dumpz0rs.png](http://upl.silentwhisper.net/uplfolders/upload2/dumpz0rs.png) (1280x1024)

I use the same resolution in Windows and it works superbly without lag... since I heard Linux would take less resources I would be suprised if this can't be fixed..,

EDIT: removed the img-tag, toooo big.

---

### Post by Kimm on 2005-06-22
well, one thing we can say is: that is not the way it should be!

perhaps you should download the drivers from nvidia.com and install them, I have a feeling it might work better.
Dont worry about it, its not a problem with Linux its probably some setting that is wrong and something that must be changed, nothing that cant be fixed.

Unfortunently I'm not enough of a &#361;ber Linux user (besides from the fact that I know most of the facts around Linux ](*,) ) so I cant tell you what to do

---

### Post by bunced on 2005-06-22
nv is the free driver for Nvidia cards, as the Nvidia can't be put into Ubuntu for legal reasons. You could probably do with installing the nvidia-glx and nvidia-kernel packages from the Ubuntu synaptic manager, as this will get rid of the lag using the correct drivers.

Then edit /etc/X11/xorg.conf using sudo and scroll down until you see the line saying "Section" "Device" A couple of lines below this you will find something like "Driver" "nv". Change to "Driver" "nvidia". Save and exit. Reboot your PC, and you should have fixed the problem

Regards,
David

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=bunced]
Then edit /etc/X11/xorg.conf using sudo and scroll down until you see the line saying "Section" "Device" A couple of lines below this you will find something like "Driver" "nv". Change to "Driver" "nvidia". Save and exit. Reboot your PC, and you should have fixed the problem
[/QUOTE]

The exact command you want is this:

gksudo gedit /etc/X11/xorg.conf

---

### Post by Trojan1313 on 2005-06-22
[QUOTE=poofyhairguy]The exact command you want is this:

gksudo gedit /etc/X11/xorg.conf[/QUOTE]
 It's fixed. :) Thanks a lot. :)

Have no idea how to do what I did another time though... :p I used a command from another tread with opened a guide to configurating X.

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=Trojan1313]It's fixed. :) Thanks a lot. :)
[/QUOTE]

Anytime.

---

