---
title: "Airlink USB 802.11g adapter, AWLL3026"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by rikc on 2007-04-07
I recently installed Dapper on an IBM Thinkpad X23, and I'm not sure how to get it to recognize my USB wireless adapter, an Airlink AWLL3026.  Searching around for help, I've learned that this adapter supposedly works out of the box with Dapper, except for the newer models, which use a different chipset.  My problem is, I can't figure out how to find which chipset I have.  I'm assuming the newer model, as I just took the laptop out for a test run and the internet was not detected, but I would of course like to know for sure.  It doesn't seem to be recognized when I run iwconfig in terminal (then again, I don't know if I'm reading it correctly).  This is my first laptop, as well as my first experience messing with wireless internet.  I would appreciate any help I could get.

---

### Post by sharke on 2007-04-07
type lsusb  in terminal and see if it lists card
If so please post output of lsusb and i will try to help.
Regards
Sharke

---

### Post by rikc on 2007-04-07
> **sharke said:**
> type lsusb  in terminal and see if it lists card
If so please post output of lsusb and i will try to help.
Regards
Sharke

Here is what I get:

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0ace:1215 ZyDAS
Bus 001 Device 001: ID 0000:0000

---

### Post by siciliancasanova on 2007-04-07
ZyDas 1215 chipset

---

### Post by rikc on 2007-04-07
> **siciliancasanova said:**
> ZyDas 1215 chipset

Is this the 'bad' chipset?  I remember reading that the AWLL3026 comes in two 'flavors,' and that one of them gives ubuntu trouble.

---

### Post by siciliancasanova on 2007-04-07
Try [this guide]("http://ubuntuforums.org/showthread.php?t=195259&highlight=Zd1211").  The chipset is different but there is a good chance it's the same problem you're having.  Just remember to change the numbers of the chipset :)

---

### Post by rikc on 2007-04-08
Okay, I did something, maybe dumb!  In another thread asking this same question, someone suggested installing Fawn, saying that it has better wireless compatibility.  I did that, and still no luck.  The adapter still shows up under lsusb, though.  Should I still try the guide you linked?

---

### Post by siciliancasanova on 2007-04-08
Yeah Feisty Fawn does have better wireless compatibility but in the case of your chipset you will still need to follow that guide.

---

### Post by rikc on 2007-04-10
Well, I finally got around to this guide, and I am in trouble in the first step.  Awesome! haha.  I enter the first set of instructions into the terminal, sudo modprobe -r zd1215
sudo apt-get remove wpasupplicant, and terminal returns this:

FATAL: Module zd1215 not found.


Fatal is good, right? :P  Any suggestions?

---

### Post by rikc on 2007-04-12
Bumping this, still not getting anywhere with that guide :(

---

### Post by nodcero on 2007-04-12
Hi,

it's my second week in Linux, so don't expect any wonders from me, but as far as I read the guide, that modprobe -r zd1215 thingy would probably have only removed your driver, if an old version had been there, so don't be discouraged by that fatal error and soldier on with the remaining steps,,,

---

### Post by rikc on 2007-04-12
That makes sense.  Soldier on I shall!

---

