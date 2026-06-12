---
title: "NVIDIA Driver Install Problem...."
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by sardopsycho on 2006-04-30
I am trying to install the linux drivers for my GeForce FX 6200 video card so I can play Doom 3 and Quake 4 - however the driver installation says I cannot install the driver in an X Window system - but I am using GNOME....so I am not sure what to do at this point.....

How do I load up into a command prompt only so I can install these drivers????

---

### Post by nudnik on 2006-04-30
control+alt+F1

type into command line : sudo -s

this will make you root

you will then need to stop xserver:

sudo /etc/init.d/gdm stop

---

### Post by nudnik on 2006-04-30
I should have mentioned that after pressing control+alt+F1 you will likely have to log back in first before attempting the remainder of my instructions.

---

### Post by wylfing on 2006-04-30
**sardopsycho** please try using the drivers that are in the Ubuntu repositories first. It is much, *much* more trouble-free than compiling them from scratch, which is what the drivers you download from the nVidia site will do. Read here:

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

