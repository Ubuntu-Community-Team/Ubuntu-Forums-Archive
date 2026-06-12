---
title: "915resolution -l command not working"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2007-06-09
i have installed 915resolution
in the terminal when i type 915resolution -l
it gives

Intel 800/900 Series VBIOS Hack : version 0.5.2

Unable to obtain the proper IO permissions: Operation not permitted

I have intel 945gz chipset with onboard graphics

please help

---

### Post by ghost_ryder35 on 2007-06-09
ubuntu doesnt regognize the card?  i thought only xubuntu didnt...  try 

sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg

---

### Post by dhawald3 on 2007-06-09
> **ghost_ryder35 said:**
> ubuntu doesnt regognize the card?  i thought only xubuntu didnt...  try 

sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg

now i have gone to 
                                                              
 Configuring xserver-xorg
 
it is asking me for
Video card's bus identifier

what do i give??

---

### Post by ramjet_1953 on 2007-06-09
To use 915resolution, you have to use it in root mode.

The correct command is:

[COLOR="Red"]sudo 915resolution -l[/COLOR]

Regards,
Roger :cool:

---

