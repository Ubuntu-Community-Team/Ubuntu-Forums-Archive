---
title: "Alternate Resolution"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by hammedhaaret on 2007-05-12
Hi.
I finally desided to install fiesty on my laptop.
my screen is 15.4" and can go to 1280x800 which makes Ubuntu look like it is being displayed on a screen several sized to small.

so im currently running it in 1024x768.
but that makes it look just a bit too streched.

so i just want to know if's possible to get a res in between, and how?

hope someone can help me
hammedhaaret

---

### Post by Biochem on 2007-05-17
It can be done by modifying the xorg.conf file

First you make a backup in case I involuntary screw up your computer 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bak

then

sudo gedit /etc/X11/xorg.conf
use kate for kde
find 
Section "Screen"
you will find a bunch of lines with codes that look like this
Modes        "1280x960"    "1152x864"    "1024x768"    "800x600"    "640x480"

replace them by the following line:
Modes        "1280x800"

save the file and press ctrl+alt+backspace or reeboot

If for any reason you cannot see a graphical interface after that, boot in recovery mode and enter the following command

sudo cp /etc/X11/xorg.conf-bak /etc/X11/xorg.conf

that will restore the original setup

good luck

---

### Post by ramjet_1953 on 2007-05-17
If you post the information about your video chipset, ie Intel, NVidia, ATI, SIS,  there is probably a driver that you can download.

Regards,
Roger :cool:

---

