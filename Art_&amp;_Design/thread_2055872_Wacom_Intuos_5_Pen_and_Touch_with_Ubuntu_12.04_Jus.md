---
title: "Wacom Intuos 5 Pen and Touch with Ubuntu 12.04 Just Works!"
date: 2012-09-10
forum: Art &amp; Design
---

### Post by BcRich on 2012-09-10
I was really surprised when I got my intuos 5 as I was expecting to spend a couple of hours playing around with drivers and xinput settings, but I was so excited when I simply plugged it into my ubuntu 12.04 machine and it just worked!
no driver installation, no messing around with xinput no tweaks.
I'm so impressed with Ubuntu, that I had to post about it here :)
Just to clarify I did use a genius pensketch (which used the wizard pen driver) on this same machine so perhaps that had something to do with it?
What I'm really impressed with, is that the touch settings including the buttons on the tablet also work (this obviously has nothing to do with the wizardpen driver). for example I can scroll with two fingers, zoom in and out and right click with a two-finger double tap in firefox. Also the scroll feature works flawlessly by rolling over the circular tablet controller. 
I'd love to know if anybody can offer a plausible explanation as to why things just work with this device, as it seems like windows and mac users have to perform the additional step of installing drivers and possibly even rebooting... btw Linux support is not mentioned anywhere on the wacom website for this product.

---

### Post by Favux on 2012-09-10
Hi BcRich,

Glad it just worked for you.  :)


I'm pretty sure somewhere on their site Wacom links to the Linux Wacom Project because I've seen the link.  Intuos5 support was added by Jason, a Wacom developer, on 4-4-12.  He works on the Linux Wacom Project:  [http://sourceforge.net/projects/linuxwacom/](http://sourceforge.net/projects/linuxwacom/)  and  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)  Jason is fairly new but he's been with the Project over a year now.  The other Wacom developer, Ping, has been with the Project a long time and for quite a while was pretty much managing the Project solo.  About 3 years ago Peter, a Xorg developer who works for RedHat, joined the Project and he is the lead developer.

Intuos5 support was added to xf86-input-wacom after 0.14.0 came out.  I think it was Timo Aaltonen, a Ubuntu developer, who backported the Intuos5 support into Ubuntu's version of xf86-input-wacom-0.14.0.

And that's the story.

---

### Post by BcRich on 2012-09-10
> **Favux said:**
> Hi BcRich,

Glad it just worked for you.  :)


I'm pretty sure somewhere on their site Wacom links to the Linux Wacom Project because I've seen the link.  Intuos5 support was added by Jason, a Wacom developer, on 4-4-12.  He works on the Linux Wacom Project:  [http://sourceforge.net/projects/linuxwacom/](http://sourceforge.net/projects/linuxwacom/)  and  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)  Jason is fairly new but he's been with the Project over a year now.  The other Wacom developer, Ping, has been with the Project a long time and for quite a while was pretty much managing the Project solo.  About 3 years ago Peter, a Xorg developer who works for RedHat, joined the Project and he is the lead developer.

Intuos5 support was added to xf86-input-wacom after 0.14.0 came out.  I think it was Timo Aaltonen, a Ubuntu developer, who backported the Intuos5 support into Ubuntu's version of xf86-input-wacom-0.14.0.

And that's the story.
Hi Favux
I was hoping you would answer my question :) 
Thanks, that certainly clears that up :lolflag:
... and thanks for inadvertently answering my second question which would be, is there a mailing list i can subscribe to keep up to date with wacom on linux support. I subscribed to linuxwacom-announce :KS:KS:KS:KS:KS

---

