---
title: "ubuntu on iMac tray loading : weird display"
date: 2007-11-26
forum: Apple PPC Users
---

### Post by gorkita on 2007-11-26
I installed ubuntu 5.04 on my iMac 233 rev.B, 96 Mb RAM. Graphic card is ATI Rage Pro.
Everything seem to work fine, except X. In console mode everything is perfect but something seems wrong with X. Some parts of the screen don't refresh... I Don't know how to explain this, so please check the [_screen cap_]("http://img266.imageshack.us/img266/7011/sanstitreyi7.jpg").

I tried the usual xorg.conf trick (see below) but no success. Same problem with xubuntu 6.06.1 BTW.
Any idea what it could be ?

[trick I tried :
4. Press CRTL-ALT-F1. This brings up the command line.
5. Now we need to edit the Xorg.conf file. Type: sudo nano /etc/X11/xorg.conf
6. Add a "#" at the line that says LOAD DRI. This keeps it from loading.
6a. Go to area near the bottom under "Monitor" and adjust the HorizSync to 60 and VertRefresh to75-117 respectively.
7. Go to the the area (towards the bottom of the file) where the default Depth is and change it from 24 to 16.
8. Save and exit out of nano.
9. Type: sudo killall -HUP gdm
10. This will kill and restart the GUI.
11. You will get a screen resolution of 800 x 600 with 16 color depth.]

---

### Post by gorkita on 2007-12-03
[IMG]http://home.tele2.fr/zest/smilies/up.gif[/IMG]

Still stuck...

---

### Post by Martin A on 2007-12-03
You probably don't need to hear this , but I've tried (unsuccessfully, I might add) to run on Ubuntu 5.10 on 3 tray loading iMacs. Slot loaders work OK, but getting any GUI situation to work on a Rev A/B iMac is likely to be a fruitless struggle. 
My advice? Go with Panther. 
Of course, that was a long time ago, and if I'm hugely mistaken and this IS possible, someone chime in here 8)

hih

Martin

---

### Post by gorkita on 2007-12-04
I was kind of scared I would hear that ;-)
Thanx anyway !

---

### Post by PaganHippie on 2007-12-04
Why not try a newer release than 5.04?  6.06 and 7.04 both work fine on my Rev A iMac.

---

### Post by gorkita on 2007-12-13
Actually I did try the newer releases, but I wasn't able to install. Something went wrong during the installation process, the installation froze at the same step, something about language pack nstallation if I recall correctly

---

### Post by oswaldkelso on 2007-12-14
> **gorkita said:**
> Actually I did try the newer releases, but I wasn't able to install. Something went wrong during the installation process, the installation froze at the same step, something about language pack nstallation if I recall correctly

The bottom line is you need more ram if you want to run k/ubuntu

other wise run a lighter linux disto

ie. [fluxbuntu]("http://fluxbuntu.org/") when its ready  would be ideal.

a  build of [slackintosh ]("http://workaround.ch/")  with a window manager

excellent install instructions though you may want to use your ubuntu disk to do the partitioning

 or [gentoo]("http://www.gentoo.org/main/en/where.xml")

not really a noobies distro but  lots of ppc users and possibly the best ppc  support (imo)

or debian my disto of choice my how to is [here]("http://forums.debian.net/viewtopic.php?t=20481")

---

### Post by gorkita on 2007-12-20
I will try these ! Thanks for the tips :guitar:

---

