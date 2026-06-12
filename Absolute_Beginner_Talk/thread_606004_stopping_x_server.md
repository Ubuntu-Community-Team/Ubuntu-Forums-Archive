---
title: "stopping x server"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Guruprasad on 2007-11-07
I want to install graphic driver for NVedia Graphic card.

Before installing we need to stop the x server.

Please let me know how to stop the x server.

---

### Post by meborc on 2007-11-07
do ctrl+alt+F2 to get to the command line... from there do "sudo /etc/init.d/gdm stop" (if you use kubuntu try kdm... or if you use fluxbuntu try slim instead of gdm)... then install the drivers...

to start the X again do "sudo /etc/init.d/gdm start"

---

### Post by LowSky on 2007-11-07
or just start the computer in safemode

then boot X with startx

---

### Post by erginemr on 2007-11-07
> **Guruprasad said:**
> I want to install graphic driver for NVedia Graphic card.

Before installing we need to stop the x server.

Please let me know how to stop the x server.

Although you can install it this way, I strongly recommend you not to install NVIDIA card driver using their site, especially under Feisty. Problems may start to arise as soon as you upgrade your kernel later on via repositories / update manager.

With the NVIDIA installer, you need to run it once again after each kernel update, otherwise you may say bye-bye to your X session. I have suffered this before, as well as another Ubuntu user as you may follow from the thread below:

[http://ubuntuforums.org/showthread.php?t=602034](http://ubuntuforums.org/showthread.php?t=602034)

Believe me there is no need to undertake that risk. You will find the binary drivers under the repositories already (see synaptic, nvidia-glx-new, nvidia-glx or nvidia-glx-legacy, depending the age of your NVIDIA card). AFAIK, the driver installed from the repositories is equally good in terms of performance.

---

### Post by HermanAB on 2007-11-07
I'm not at an Ubuntu machine now, but won't this stop X:
$ sudo init 3

---

