---
title: "Nvidia GEForce 4 MX440  install? x server prob"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by davencarla on 2007-04-25
Can anyone help me install an Nvidia GEForce 4 MX440 video card?

When I put in the card and start up computer I get:

Failed to start X server (your graphical interface).  It is likely that it is no tset up correctly......

What do I do?

Thanks!

---

### Post by annda on 2007-04-25
is it a second card? a substitute for the one you used to install/configure your ubuntu? an extra card to an on-board chipset?

X is having problems because it is configured to use a different card and doesn't recognize the new one.

---

### Post by davencarla on 2007-04-25
it is a second card to the intergated video that ubuntu was setup with

---

### Post by annda on 2007-04-25
i think the best idea would be for you to disable the integrated on-board chip in BIOS settings and then boot into recovery when you get the option to choose kernel and operating system in GRUB, and reconfigure your X server using this command:

dpkg-reconfigure -phigh xserver-xorg

when you are asked about the driver, choose 'nv'

you will need to install/reinstall nvidia driver from synaptic later, when you have the X server running.

---

### Post by mmikelst on 2007-04-25
Alternatively, assuming you're having the same type of error I had with my nvidia card, try editing your xorg.conf file, make sure it's using the right drivers.

---

