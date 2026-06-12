---
title: "which version for old PPC G4?"
date: 2012-03-23
forum: Apple Hardware Users
---

### Post by awesomemac on 2012-03-23
Hi,


I have an old PPC G4 mac with 500 MHz and Maxed RAM (about 2 GB) and I'd like to know if I could get ubuntu for this mac. As far as I know, RAM is sufficient, but the Processing Speed is pretty low. Which version of ubuntu can I get on this mac? Thanks!!!!!

---

### Post by beanhead on 2012-03-23
Well you have a PPC processor and if you want to install xubuntu you have to have a os9 disc for your mac. 
the guide is here 

[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

---

### Post by awesomemac on 2012-03-23
I do not have an oldworld mac (at least I don't think so.....), the page says that all G4s are newworld macs. I do have mac OS 7, 8, and 9 CDs but I'd like something a bit more modern, not 10 year old stuff.

---

### Post by beanhead on 2012-03-23
Then i would suggest runnig the 10.04 version here
[http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/)
the desktop version on the top of the list.

There is an installation guide here 
[http://lowendmac.com/crews/05/1214.html](http://lowendmac.com/crews/05/1214.html)

---

### Post by MisterGaribaldi on 2012-03-23
If you can, maxx out the RAM on that computer. If possible, see if you can replace the graphics card with something a touch more modern (but you'll be limited because the G4 towers at best had AGP slots).

Other than that, Gnome will probably work just fine on it, but you could (as suggested above) go with XFCE or some other less-demanding GUI. That should help you out tremendously.

Also, remember that Flash does not exist for Linux/PPC. You can probably get by with something like Gnash, but also remember that the underlying Flash technology is optimized for Intel-based (that is, x86) processors, and is going to be pretty sluggish on G3/G4/G5 systems.

At some point, you might consider retasking this computer as a server. If you do that, you'll find it handles being a server most adequately, particularly if it's running Linux. I use Debian on a Mac mini expressly for server purposes, and it's the most solid server I've ever worked with (better than anything Apple's put out, and better than the stuff I've used in the past from Microsoft). Just saying.

Good luck!

---

### Post by awesomemac on 2012-03-23
My RAM is maxed at 2 GB. upon downloading and burning the ISO I downloaded, I get a grey screen upon booting. I'm guessing I need an xorg-conf file for the CD. Can I edit the CD to use the Xorg-conf file for my system?

---

### Post by beanhead on 2012-03-24
Are you holding The C key when you boot ?
Another way is holding command+option+shift+delete.

---

