---
title: "bcm43xx preventing install"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by n2oboost1 on 2008-03-19
I'm pretty sure I've read every single thread on how to get the bcm43xx: error: microcode fixed, but I can't do anything they say, because I can't even get into Ubuntu to run the terminal.  This error code is preventing me from installing Ubuntu altogether.  I boot the CD, select 'Run or Install Ubuntu'  the screen loads, runs through everything, then dies, right at the bcm43xx error message, nothing is installed, and I have to turn it off.  I really need some help.

---

### Post by Dr Small on 2008-03-19
Can you disable your broadcom card via the BIOS setup utilty ?
See, I'm not sure if you are running a desktop or a laptop, so either that suggestion or pull the card (which isn't possible on a laptop, I don't think).

Dr Small

---

### Post by handydan918 on 2008-03-19
> **Dr Small said:**
> Can you disable your broadcom card via the BIOS setup utilty ?
See, I'm not sure if you are running a desktop or a laptop, so either that suggestion or pull the card (which isn't possible on a laptop, I don't think).

Dr Small

might be a good suggestion. if you can't pull the card, you may be able to switch it off if it's a lappy.

---

### Post by Dr Small on 2008-03-19
> **handydan918 said:**
> might be a good suggestion. if you can't pull the card, you may be able to switch it off if it's a lappy.
I disabled that broadcom pain on my laptop, bought a sutible card (dlink) and now she works like champ.

---

### Post by handydan918 on 2008-03-19
> **Dr Small said:**
> I disabled that broadcom pain on my laptop, bought a sutible card (dlink) and now she works like champ.

I have a bm4318 and it worked out of the box with Mepis 7!

---

### Post by igknighted on 2008-03-19
That error will keep coming up, but it is completely unrelated to what is keeping your xserver from loading.  Run 'sudo dpkg-reconfigure xserver-xorg' when you get dumped to the terminal (where that error keeps coming up), and then choose 'vesa' as your driver and also a safe resolution (800x600 or 1024x768... just for now).  Everything else can be default.  Then type 'sudo /etc/init.d/gdm restart' or 'startx' when done to load X.  From there you can use restricted driver manager to install the firmware for the broadcom card to stop that message.

PS: if the message gets too annoying as it keeps popping up, use ctrl-alt-F2 to get to a new terminal screen where it shouldn't.

EDIT: What are your specs... we might be able to pinpoint why the xserver isn't loading.

---

### Post by n2oboost1 on 2008-03-20
I have tried turning off the card with the external switch and still got the message.  I am running an HP Pavilion dv6000 (Model dv6609wm) laptop.  1.8 GHz, 1GB of RAM, AMD 64 Dual Core Processor tk-55.  Anything else you need?  Please let me know.

---

### Post by n2oboost1 on 2008-03-20
Also, I do have an external wireless card I can use if that's what you recommend.

---

### Post by n2oboost1 on 2008-03-20
Anyone?

---

