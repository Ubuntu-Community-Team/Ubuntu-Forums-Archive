---
title: "Getting Belkin Wifi Card Up and Running"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by TeuchterNYC on 2007-06-02
I'm completely new to ubuntu and linux - just finished installing it on my hard drive. My wireless card is not recognized and I have no idea how to go about making it work. The lights do not come on on the card. I have a Belkin Wireless G notebook F5D7010 card  I assume I have to find an appropriate driver to install. Any pointers would be appreciated.

---

### Post by chamberlain2006 on 2007-06-02
Ok.  First, can you open up terminal (Applications>Accessories>Terminal) and post the output of "lspci" (if your card is internal) or "lsusb" (if your card is usb).

---

### Post by Mr_bleu on 2007-06-03
I have a belkin usb card I could not get working.  Right now I'm reinstalling and I could access lsusb.
:Bus 005 Device 004: ID 050d:705a Belkin Components 
With the system installed I could never get to this info.

---

### Post by Mazza558 on 2007-06-03
Try this...

After installing it, simply restart and you're done. This applies to both people having trouble.

:)

(Just so you know, all Belkin Wireless Devices use this driver - it just isn't installed by default.)

---

### Post by Mr_bleu on 2007-06-03
My desktop environment will not start with the usb adapter plugged in.  I can log in, then llllllllllllllllooooooooooooooonnnnnnnnnnnnnnnnnnggggggggggggggggggg boot.  I can't wait that long to see if it boots.

---

### Post by pappapump on 2007-06-03
Well mines running but wth is wrong with it?
It says I have the right driver installed and ndiswrapper is a bust.
Heres a screenshot.
I tried everything an it just won't connect.

---

### Post by Austin_KW on 2007-06-03
> **Mr_bleu said:**
> My desktop environment will not start with the usb adapter plugged in.  I can log in, then llllllllllllllllooooooooooooooonnnnnnnnnnnnnnnnnnggggggggggggggggggg boot.  I can't wait that long to see if it boots.

For the USB, it is loading most likely loading multiple incompatible drivers, none of which actually work. If it is the version 300x usb adapter you need to follow the instructions at [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236), Even if it is not a ralink rt2571/rt73 chipset you will need to follow the part of the instructions to blacklist the rt2570 and rt73usb drivers.

---

### Post by TeuchterNYC on 2007-06-03
My card fits in the PCMCIA slot on my laptop. Is that internal or external or something else?  What are "Isusb" and "ispci". I tried typing each at the Terminal command prompt and got nothing (probably wrong directory), then tried to find such a file, but am still pretty hapless with UNIX as I haven't used it in many years. I guess my question is what are "Isusb" and "Ispci", where can I find them and are they appropriate for a PCMCIA wireless card? Thanks.

---

### Post by TeuchterNYC on 2007-06-03
Oh, oh - I missed Mazza558's reply that included the driver. How do I go about installing this driver (when giving instructions for this, please assume I have not seen let alone touched a computer before today....;-)

---

### Post by TeuchterNYC on 2007-06-03
Ok - so I double click on it to install it......who'd of thunk it.

---

### Post by Mr_bleu on 2007-06-03
Thanks, It's working now........................................................:D yeehaw!!  
It's just a backup wifi, but it's nice to have it working.  I have onboard wifi via intel 3945 chip.

---

### Post by Mr_bleu on 2007-06-03
This guy's how to has mine working.
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

