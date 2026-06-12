---
title: "Swaping video cards"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-04-07
I have a Dell 4100 desktop, with an ATI Rage Pro 128 video card. Dapper was installed under that card. I want to remove it and install an Nvidia FX5200. The HCL says it works, but what will  happen if I just switch cards? Can X-org be up and running, can it recognize the 5200? What is the safest way to do the swap? Use A/X to download the nvidia driver first, before removing the ATI card? How, please.

---

### Post by ed-j on 2007-04-07
Hi !

I'm not sure if you have to download drivers? Have a look in Add/Remove in dapper before you make the switch, you may find Nvidia binary drivers there. I have experience that they are there in Edgy.

Hope this helps! :-)

---

### Post by Mark_in_Hollywood on 2007-04-07
What am I looking for in Add/Remove? I had a look for 'ati' and 'nvidia' and nothing helpful was returned. If you have an fx5200 did you change it from or to another card, please?

---

### Post by ed-j on 2007-04-08
I have only used an FX5200 with Windows. I use an ATI Expert PRO 2000 with Breezy (5.1) and a 7600GS with Edgy and KDE 3.5. To get my GS up and running, I loaded the binary drivers (nvidia upto date drivers) in Add/Remove then set up the xserver through the command [COLOR="Teal"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

Sorry for the delay, I've been offline.  :-)

---

### Post by richbarna on 2007-04-08
This script will install the nVidia driver for you :-
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Automatix2 will also install the drivers for you :-
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by ed-j on 2007-04-08
:guitar: Gercha! :)

---

