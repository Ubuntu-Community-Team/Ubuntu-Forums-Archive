---
title: "Gutsy screen problem"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by railpostau on 2007-11-16
Laptop:
Compaq Presario V6000
AMD 64 CPU
NVIDIA Chipset
NVIDIA Graphics..

Dual Boot with XP..

Gutsy 7.10 AMD64 Iso downloaded from Ubuntu (16.11.07)

Problem is on install of Gutsy the whole process goes fine until after settings are loaded and then I get a black/dark grey screen with no mouse pointer or any form of discernable icons writings etc..

Same machine loads SIDUX, Kanotix, Mepis, Puppy and Knoppix without screen problems..

Any suggestions:

Have tried

1. Setting VGA at 800x600 (16 and 32)
2. Safe graphics settings on load
3. Boot options set to casper quite
4. Manufacturer OEM Install

either combined or seperatley..

Nothing seems to work

Any solutions

Thanks

---

### Post by overdrank on 2007-11-16
HI and welcome you may try and boot into recovery mode.enter this command in the terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command reboot.  Hope this helps and good luck!

---

### Post by maxxum on 2007-11-17
I have had this issue and a quick forum search showed that when you see the boot screen from the livecd, press F6 and type in the word noapic at the end of the command line. Press enter. The black and grey lines will momentarily appear and then you should see the desktop.

---

### Post by railpostau on 2007-11-17
I would like to try that but a blank screen is all I have to work with, so it is a little difficult to see what and where I am typing etc..

Thanks for your help..

Have gone back to SIDUX which at this moment has loaded etc with no problems.

Will try Ubuntu again in 3 or 4 distros time...

See ya

---

