---
title: "Help, Screen resolution"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by pencil86 on 2007-08-25
I finally managed to install the Linux drivers for the Nvidia card. How do I adjust the screen resolution? When I goto the screen resolution setter, it only shows upto 800x600.....even though both my graphic card and monitor support resolutions of 1028x1024.

How do I set it to 1028x1024? Also, the nvidia driver appears in "Restricted Drivers" program...is that safe?

---

### Post by alienexplorers on 2007-08-25
Did You Load the nvidia-settings program.  If so you can use it to change your screen resolutions.  To run it type in terminal:
> gksudo nvidia-settings

---

### Post by sonicborg on 2007-08-25
please can you post your xorg.conf file. i am trying so hard to get my nvidia card working after swapping from ati. its doing my head in.
also what did you need to install, and where did you install it from please (synaptic? which files?)
thanks

---

### Post by pencil86 on 2007-08-25
I loaded the nvidia-settings program but I do not see the "resolution" set tab/option...?

---

### Post by alienexplorers on 2007-08-25
Try loading the drivers using the ENVY script located at:
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by sonicborg on 2007-08-25
tried them myself. and envy is just struggling  to do anything... posted error here 
[http://ubuntuforums.org/showthread.php?t=534655](http://ubuntuforums.org/showthread.php?t=534655)

---

### Post by pencil86 on 2007-08-25
Envy fixed the problem BUT why didn't the resolution options come by DEFAULT when I installed the driver? What did Envy do to put the option in the Nvidia settings that I didn't do??

---

### Post by sailor2001 on 2007-08-25
gksudo nvidia-settings
click server display settings

---

