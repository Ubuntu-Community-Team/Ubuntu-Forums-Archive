---
title: "Nvidia Drivers - Ouch!"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Drevix on 2007-08-31
I am having an absolute nightmare trying to get the correct video drivers installed on my system. Does anyone know what the correct 96xx driver file is for a GeForce4 MX 440 on Ubuntu 7.04 Feisty? I tried the 9631 and it was incompatible with my Kernel. There's a few 96xx files on the Nvidia website and I don't know how to tell which one will work with my Kernel.

Thanks!

---

### Post by Lord Illidan on 2007-08-31
Try installing nvidia-glx-legacy from Synaptic.

---

### Post by alienexplorers on 2007-08-31
Try using the ENVY script located at:
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I have used this at least 5 times and never had a problem and my nvidia card runs great.

---

### Post by Crafty Kisses on 2007-08-31
> **alienexplorers said:**
> Try using the ENVY script located at:


I have used this at least 5 times and never had a problem and my nvidia card runs great.

That should do the trick.

---

### Post by Drevix on 2007-08-31
Thank you. That worked very well without any problems. It's a nice relief to have a better resolution, a refresh rate of 50Hz is awfull. I was running around in circles trying to do it manually and I'm just not ready for that stuff yet.  At least I learned how to fix a messed up xorg.conf from the command line. :-)

---

