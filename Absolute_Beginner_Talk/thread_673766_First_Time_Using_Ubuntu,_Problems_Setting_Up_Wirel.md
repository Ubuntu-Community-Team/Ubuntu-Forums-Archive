---
title: "First Time Using Ubuntu, Problems Setting Up Wireless"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by gtdott14 on 2008-01-21
Alright.  I know what some of you might say... "Go search the threads" but I have and I've tried many tutorials out there but my wireless still doesn't seem to be working.

I've wiped clean my HP Pavilion zv5000 and have installed Ubunutu 6.06 LTS on it.  I have a Broadcom BCM4306 802.11b/g Wireless LAN chipset.  It's a 3.2ghz Pentium 4 machine.

I've tried so many tutorials and have ndiswrapper installed I believe.  I can see my wireless card in the networking options as eth1 and it is active. I have in the properties my SID and passphrase for the wireless but in the top right hand corner, in my connection properties, it still says my connection name is "lo" and the status is "idle".

If you need any other information from me, let me know. I can't wait to get all this working right!

---

### Post by smartboyathome on 2008-01-21
I would suggest using 7.10 if possible, because 6.06 is going to be 2 years old this year, and is quite dated. 7.10 also has better support for wireless cards.

---

### Post by gtdott14 on 2008-01-21
> **smartboyathome said:**
> I would suggest using 7.10 if possible, because 6.06 is going to be 2 years old this year, and is quite dated. 7.10 also has better support for wireless cards.

I tried downloading that and installing it but it came with an installation error.  I then checked my disc that I burnt it on and there was an error on the disc, so I re-burned it and the same thing.  So I was thinking there was an issue with the download from the site.  Did you get it from the site and have any problems with installation? Should I try re-downloading it?

EDIT: I just did a hash check and it was not equal to the one posted on the site.  I will re-download it.

---

### Post by gtdott14 on 2008-01-21
I got the internet working. Now I'm just tyring to get adjusted to everything and perhaps install Beryl.  Thanks :)

7.10 I guess will not install unless you do a manual install and partition your hard drive that way.

---

### Post by stalkingwolf on 2008-01-21
I have downloaded 7.10 and installed it with no problems.  I also find that in some cases 7.04
works better.  You could order the free cd from the site.

---

### Post by smurphy_it on 2008-01-21
Don't bother downloading beryl.  It is old and has been replace by compiz.  It is already installed with Gutsy 7.10.  Just go into a terminal and type *[COLOR="RoyalBlue"]sudo apt-get install comizconfig-settings-manager[/COLOR]* to get the application for compiz where you can change all of the effects (like adding a cube, etc).

Also for wireless you could try the restrictred drivers.  They are usually only 24Mb.  For you full 100Mb you will have to use ndiswrapper (native might do it too!).

For the restricted drivers, just click on System, Administration, Restricted drivers manager.

---

