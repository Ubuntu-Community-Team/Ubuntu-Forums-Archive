---
title: "Install Nvidia"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-09-02
I don't want to use nvidia-glx, instead the latest from nvidia.com. I run sh NVIDIA and press tab etc. and it says i need to specify the kernel-source path? What is the path?

---

### Post by goatflyer on 2007-09-02
I struggled so much with the official NVIDIA instructions,  I gave up and installed envy.  You might want to try it too, get it here:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)


It does everything from detecting your nvidia card, downloading latest driver from nvidia, detecting your ubuntu kernel, downloading the correct kernel header files, compiles the driver, installs it, then prompting you to modify your xorg files (say yes), then prompts you to reboot (say yes).

And if and when there is a kernel update, and perhaps the nvidia in the repos isn't updated, envy will still help you.  When your new xorg ever refuses to come up, just use envy's text interface  "envy -t" and it will do everything the graphic version does, only in text mode.  The result is a happy nvidia install.

---

### Post by MenZa on 2007-09-02
What's wrong with nvidia-glx?

---

