---
title: "graphix drivers"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by ezek on 2006-08-21
Hey, im backing up some stuff as i type, but before i install ubuntu i was wondering of a good site to download graphic card drivers for linux. I have a Nvidia 6800GT. 1 more question. Will all games by ID software work with unbuntu? I would like to get Quake 4 and Doom 3 for my comp. Can i just pop of in and they will install?

---

### Post by tuxcantfly on 2006-08-21
nvidia drivers can be installed like this:

sudo apt-get install nvidia-glx
sudo nvidia-xconfig

reboot, and you're done. yes, all id games will work.

---

### Post by bodhi.zazen on 2006-08-21
Not sure about your games, I am not a gamer.

You can get the graphic drivers from two sources:

1. Synaptic (search for nVidia). This is the "open source" driver. 

2. It did not work with my nVidia 7600 so I downladed the nVidia driver:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

The nVidia driver is proprietary but it works.

---

### Post by tuxcantfly on 2006-08-21
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

is a more detailed guide on installing nvidia drivers

---

### Post by tuxcantfly on 2006-08-21
don't bother using the drivers from nvidia's site. nvidia-glx is the same thing, and is far easier to set up and update

---

### Post by bodhi.zazen on 2006-08-21
> **tuxcantfly said:**
> don't bother using the drivers from nvidia's site. nvidia-glx is the same thing, and is far easier to set up and update

Ulness nvidia-glx does not work with your card (as is my case).

---

