---
title: "I cant get the live CD to start"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by cbgeek12 on 2008-03-17
I boot from the live CD and it says ubuntu is running in low graphics mode.

I have the AMD64 desktop ISO.

My graphics card is from NVIDIA and I have AMD Turion.

It is a Compaq Presario F700 Laptop.

Can someone help me?

---

### Post by spiderbatdad on 2008-03-17
Maybe able to add some parameters to the kernel boot line by pressing F6 at the options screen... for example delete "ro --quiet splash" and replace with "noapic nolapic vga=792"  You may need all or only vga=792. There may also be a vga config setting in your bios

---

### Post by uberlube on 2008-03-17
I have the Compaq Presario f500 and i have to use vga=791 to get it to work.

---

### Post by spiderbatdad on 2008-03-17
791=1024x768 16bit
792=1024x768 24bit color
795=1280x1024

---

### Post by ameseisch on 2008-03-20
once you get to the screen where it says start or install... select the start in safe graphics mode.

you graphics card is still not really detected but it at least gets gnome going. WiFi and sound won't work with out some serious manipulation.

I am pretty disappointed with  Ubuntu on this machine. maybe its just a little to new or something

---

### Post by cbgeek12 on 2008-03-20
I tried safe graphics mode in a virtual machine and it does not give me the panels, just an icon that says "install"

---

