---
title: "Messed up Xserver"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by arochester on 2007-01-15
I have messed up Xserver. I have had Nvidia drivers and Nvidia beta drivers, now I can't install either. I have tried the command > sudo apt-get install --reinstall xserver-xorg
... but it refuses to do so and says "not updating /etc/X11/X; file has been customized."

Either I need to clean out the directory, without deleting anything critical, or, if I can, do a clean reinstall of it.

How?

---

### Post by bigken on 2007-01-15
try sudo dpkg-reconfigure xserver-xorg ;)

---

### Post by arochester on 2007-01-15
I have tried that in a text mode . It gives me another backup file - I have about a dozen - but it doesn't seem to clear the problem.

---

### Post by bigken on 2007-01-15
this does not give a backup file but gives you a new xserver of default settings

---

### Post by bigken on 2007-01-15
just select vesa as your driver this will at least get you to your desktop

---

### Post by arochester on 2007-01-15
I have the graphical desktop - I just can't get Nvidia to load and run anymore.

---

### Post by bigken on 2007-01-15
use automatix to install the drivers for you its the easiest way

---

### Post by arochester on 2007-01-15
I have Automatix2. It said that Nvidia driver was installed (but it wasn't working). Deinstalled it. Reinstalled it. Computer crashed to text level.

When I do a reconfigure it says the card is "nv" rather than Nvidia. I have tried the bit about changing nv to Nvidia - but that didn't work either.

---

### Post by bigken on 2007-01-15
did you reboot after you remove the drivers

---

### Post by arochester on 2007-01-15
Yes. It told me to reboot.

---

### Post by bigken on 2007-01-15
ok I would try this run the sudo dpkg-reconfigure xserver-xorg and select vesa 
as your driver then try and install the nvidia drivers via automatix 

sorry I cant help you anymore

Im sure if you do a more indepth search of the forum you find your answer

---

### Post by r4ik on 2007-01-15
For drivers you could try,

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

Good luck !

---

