---
title: "Driver mess-up problem"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by federicotedin on 2007-06-26
Today i tried to install drivers for my NVIDIA GeForce FX 5500 using ENVY.  It f*cked up the x server system.  I somehow repaired it using the sudo dpkg-reconfigure xserver-xorg by selecting the NV and hitting enter when i didnt know what to put (most of the times).  Now i cant play any 3D games, they crash (like Nexuiz).  Before the restricted drivers manager detected my video card and it was activated.  Now I go to the restricted drivers and it tells me that my hardware doesn't need it.  I need help PLEASE, any answer? The PC finds the card (in hardware info) but it is useless.  Please help me to go back to the restricted drivers!

thanks

---

### Post by federicotedin on 2007-06-26
I forgot to mention that beryl worked normally before, and now it doesnt even start.  looks like my 
PC lacks of any tipe of 3D animations
thnx

---

### Post by overdrank on 2007-06-26
> **federicotedin said:**
> Today i tried to install drivers for my NVIDIA GeForce FX 5500 using ENVY.  It f*cked up the x server system.  I somehow repaired it using the sudo dpkg-reconfigure xserver-xorg by selecting the NV and hitting enter when i didnt know what to put (most of the times).  Now i cant play any 3D games, they crash (like Nexuiz).  Before the restricted drivers manager detected my video card and it was activated.  Now I go to the restricted drivers and it tells me that my hardware doesn't need it.  I need help PLEASE, any answer? The PC finds the card (in hardware info) but it is useless.  Please help me to go back to the restricted drivers!

thanks

Hi you can try this command in the terminal *sudo dpkg-reconfigure -phigh xserver-xorg* It will automatic configure your xorg and hopefully get you back!:popcorn:

---

### Post by w4ett on 2007-06-26
Go to Synaptic and install  the nvidia-glx-legacy, nvidia-glx, or the newest nvidia-glx-new I believe.

---

### Post by federicotedin on 2007-06-26
Ok, i run it , selected nv and the default resolutions... gonna reboot now THANKS

---

### Post by federicotedin on 2007-06-26
the 3D applications still dont run, now ill go to synaptic (didnt see the post)

---

