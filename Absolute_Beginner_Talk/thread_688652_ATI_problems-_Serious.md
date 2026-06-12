---
title: "ATI problems- Serious"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by thechappy on 2008-02-05
After extensive searching I have come to the conclusion that my problem is a bit unique and that it may not have a solution. 

I installed Ubuntu Gutsy nearly a month ago, and though I have had to work through many problems, it has worked for the most part, and I've been happy that I kicked windows off the Laptop.

Then yesterday I needed to restart the computer, and when it loaded back up, the GUI didn"t come up, just a black screen with the busy cursor. I went into the console and ran a slew of commands including:

sudo dpkg-reconfigure xserver-xorg

manually configured xorg.conf

ran /etc/init.d/gdm restart and stop when it didn't work

then startx, which only made a pixelated splash screen blink a couple of times, then back to console.

It should be noted that any changes made in reconfiguration have been changed back as they did not solve the problem.

I tried booting from the CD, and there I get an error
hdc: error code: 0x70 sense_key 0x03 asc:0x11 ascq: 0x05

I have tried various things to fix both problems, but really, is the graphical interface and the DVD drive problem that closely related? 

Obviously I can't fresh install, and I really don't want to anyway. Help is appreciated.

Toshiba Satellite a105 s1014
Intel Celeron M 380 1.5 GHz
60 GB Serial ATA
ATI RC410 Radeon Xpress 200m
15.4" WXGA TFT w/ TruBrite (Resolution: 1280 x 800 pixels)
Cannot find the manufacturer of the CDRW/DVD drive

---

### Post by spiderbatdad on 2008-02-05
all i found on this were several bugs reported to launchpad...with no apparent work around.```
cat /etc/fstab
```see if something looks wrong. Have you tried booting into recovery...then ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Is there a config for pci in your bios? or a screen config in bios?

---

### Post by thechappy on 2008-02-06
I have ran

> cat /etc/fstab

but I didn't notice anything out of the ordinary.

> dpkg-reconfigure -phigh xserver-xorg

change nothing. No change in the bios has solved any problems. Does anyone have anything else?

---

### Post by spiderbatdad on 2008-02-06
just reading in another forum that if your username contains a space, it can cause ubiquity to crash. I dont know if you have that space...but ubiquity crashing is your problem.

---

### Post by thechappy on 2008-02-06
No space, but at least I have another lead! 

Thank you.

---

### Post by thechappy on 2008-02-06
Then again.. not actually having ubiquity very neatly erases it from being the source of the problem. :)

---

