---
title: "Ati Radeon 9200Se"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by projectgonewrong on 2005-12-26
Okay I put it in my computer I started it up and it didnt work tell me step by step how to get it to work. I took out the card for  now so i could start it up. please

---

### Post by Remmelas on 2005-12-26
well.  Put the card back in.  X 'should' fail to load and dump you to a console screen.  log in, and do 
```
sudo apt-get install fglrx-control xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg
```

here's a link to how i set mine up
[https://wiki.ubuntu.com/MikeBedwell#head-8d46121407a74bb858ea1b24dba709930c581705](https://wiki.ubuntu.com/MikeBedwell#head-8d46121407a74bb858ea1b24dba709930c581705)

---

### Post by Landice on 2005-12-26
Doesn't the system will auto configure it during the installation? Hmm.. not very sure.. My ATI 9500 is working fine.. but i wonder am i still need to download a linux version driver for it, coz it seems a bit laggy when i'm playing games in linux.. (only the default normal games..) :(

---

### Post by bavs on 2005-12-27
i have given up
ati 9200 works fine with fglrx till i install my wireless card with madwifi... then i am unable to load as it crashes at login screen.
went to recovery console reconfigured and then removed wireless then i seem to start ubuntu breezy fine. i have been through this for a few days not knowing y it crashes and now i know its the wifi card :S 
so if you are configuring wifi then u get trouble :S and i have no idea why

---

### Post by poofyhairguy on 2005-12-27
> 
sudo dpkg-reconfigure xserver-xorg


Then pick

"radeon" driver. Made for that card- best open source graphics driver in existance!

---

