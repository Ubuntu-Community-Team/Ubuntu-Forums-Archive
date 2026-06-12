---
title: "ubuntu wont boot - missing intel driver"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by rpzatkof on 2008-01-29
running ubuntu and i'm new to it


gets stuck at boot and when i press ctr+alt+f2 to get to the terminal i can log in and do whatever


i got told to do:

sudo -s
startx


and this produced the errors

using config file /etc/x11/xorg.conf

(EE) Failed to load module "intel" (module does not exist, 0)
(EE) No Drivers Available

Fatal Server Error
    No screens found

---

### Post by jordanmthomas on 2008-01-29
Try to install xserver-xorg-video-intel
```
sudo apt-get update
sudo apt-get install xserver-xorg-video-intel
```
This should install the intel video drivers.

---

### Post by tizza10 on 2008-01-29
Log into a terminal again and (ctr+alt+f2), login as your user and type sudo dpkg-reconfigure xserver-xorg

A blue screen should come up
Use the TAB, ENTER and SPACE bar to answer any of the questions, the default values are usaully correct and let us know how you got on.

---

### Post by rpzatkof on 2008-01-29
finished through that and i get different errors this time  (i am using intel 965 express chipset family on a latitude laptop) 


i filled everything out ot the best of my ability


and i end up with 


(WW) I810; No Matching device section for instance (BUSID PCI:0:2:1) found
(EE) No devices detected

---

### Post by tizza10 on 2008-01-29
I am guessing you have an exotic laptop/motherboard/screen combination? Maybe you could fill us in on the details of your hardware, Ubuntu version etc?
 If you have a wired internet connection which is working automatically,  run "sudo apt-get upgrade" from the command line and reboot. Intel graphics have very good linux support, unfortunately the laptop manufactures do not. It takes time and/or a little work to make the newer chipsets work, but they do work!

---

### Post by rpzatkof on 2008-01-29
I'm running the latest version of ubuntu (gutsy i believe)   i don't have a wired connection now but I will later and i will run that 

I'm running Dell latitude D830 
4GB's ram and 2.1 dual core processor
dual booting vista & gutsy
I have an external monitor when I hook it up (not always) but other than that nothing exotic
Dell express chipset 965 - graphics card

not sure what else you might need to know but please let me know and i'll be able to get you the information

---

### Post by rpzatkof on 2008-01-29
oh and just curious - i've had the ubuntu cd in the drive for a while now and is that where its trying to update the drivers from or is it going online and downloading it from somewhere??

  odd question i'm just really new to linux

---

### Post by rpzatkof on 2008-01-29
another thing that I would like to add is that I just installed linux a few days ago and i'm not worried about losing settings   would it be better to just re-install linux - or is there a system reset restore or something of the sort?

---

### Post by tizza10 on 2008-01-29
If you were to reinstall the software (and sometimes this helps) ensure you do a media check on the CD you are using and ensure you do a full install.
To do the update and install the latest intel driver you need to have a wired connection to the internet.

---

### Post by rpzatkof on 2008-01-29
i solved it earlier today - when i was running sudo apt-get update it was updating from the cd (which wasn't there) - i needed to change the settings so that it was looking online for updates (i had a connection and just assumed it went online)

---

