---
title: "Ati Radeon 9200AGP - fglrx- mesa - problems"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by SreckoMicic on 2007-11-08
Ok, as hundred posts in here I got same problem, I went through dozens of installing steps, do manual install of ati drivers but nothing helped.
I just can't use fglrx drivers, is it posible that my card isn't suporrted any more, cause when I try to enable restricted drivers, manager reports that I do not have hardware that need restricted drivers, so I can only use ati driver then. When I manually put fglrx drivers in xorg and reboot, I always go to low graphic mode. So only to use 'ati' driver.
But i can't enable direct rendering or use 3d accelration (I mean not Mesa). I saw various guides, but everything is with fglrx drivers wich I'm unable to use!
I'm so confused now, just if anyone can help me with this, if anyone know is this possible.
I'm using Radeon 9200SE AGP on Gusty, and it has been working (without this mesa stuff) on earlier releases. And I upgraded from Fiesty.
I'm very depended on this, cause I'm using Blender a lot, and it crashes on me always. Of course any other software that depends on OpenGL.

---

### Post by SreckoMicic on 2007-11-08
Just to inform that I manage to revert to radeon driver which is now working nice, got some problems with compiz, but at least it is working. Now I;m gonna see what will happen with software I'm using.
And force my AGP card as PCI with: 'Option "BusType" "PCI"'. I get rid of fglrx drivers and no more mesa problems, and I have now direct rendering for a first time.

I'm using this how to to setup these open-source drivers.
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by SreckoMicic on 2007-11-13
Well, now I gonna say something I thought I will never sad but for this machine, that I'm working in office, is goodbay Ubuntu. After joy that I did something, I realize that Blender and some OpenGL  programs are useless with these open source drivers. I can't use ATI ones, because my card is not supported anymore (Radeon 9200). Luckily I got other two machines, newer, so Ubuntu will stay with me :) But for this older one, it is time to go back on WinXP. 
Sad story ......
:popcorn:

---

