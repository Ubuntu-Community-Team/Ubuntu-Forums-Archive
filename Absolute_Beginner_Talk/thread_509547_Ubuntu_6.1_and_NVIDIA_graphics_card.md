---
title: "Ubuntu 6.1 and NVIDIA graphics card"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Advocate on 2007-07-25
I'm having issues with my Ubuntu 6.10 and NVIDIA GeForce 7600GTOC graphics card.  I am using the NVIDIA-Linux-x86-100.14.110pkg1.run driver from nvidia.com.  The problem is, whenever I restart my system I have to reinstall the graphic card driver.

The error message reads:

> (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly.  Please consult the NVIDIA README for details.  Screen(s) found, but none have a useable configuration.

Fatal server error:
no screens found

The weird thing is, if I reinstall the driver and restart the gdm Ubuntu works fine until I restart the whole system.  Any help would be appreciated!  Thank you :)

---

### Post by Daveth on 2007-07-25
how did you install the Nvidia driver?

---

### Post by dpar on 2007-07-25
When I was runniny Edgy, I didn't use the .run package from Nvidia. I installed the nvidia drivers with Envy [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
 I had no problems at all with the nvidia drivers after that.:biggrin:

---

