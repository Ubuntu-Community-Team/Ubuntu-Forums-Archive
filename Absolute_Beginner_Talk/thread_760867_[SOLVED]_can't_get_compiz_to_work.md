---
title: "[SOLVED] can't get compiz to work"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by tad1073 on 2008-04-20
```
:~$ compiz
Checking for Xgl: not present. 
FATAL: Error inserting battery (/lib/modules/2.6.24-15-generic/kernel/drivers/acpi/battery.ko): 
Operation not permitted
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

Nvidia Geforce 6200 OC card w/ 256 MB DDR memory

---

### Post by skymera on 2008-04-20
Ok have you got the driver installed?

If so, how did you go about installing it?

---

### Post by tad1073 on 2008-04-20
I installed through synaptics 

```
nvidia-glx-new
nvidia-new-kernel-source
nvidia-settings

```

---

### Post by skymera on 2008-04-20
I do it this way, works 100% every time.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Download EnvyLegacy for 7.10 and below.
Download EnvyNG for 8.04

Install the .deb and run Envy.
From there follow the instructions and it will correctly install your 6200 driver.

---

### Post by tad1073 on 2008-04-20
didn't work. resolution at 800x600, broke wireless, no compiz etc.

---

### Post by skymera on 2008-04-20
Run again but choose to manually install the driver.
Which i believe is legacy.

*Results May Vary* :lol:

---

### Post by tad1073 on 2008-04-20
the driver is installed now but I can't get compiz to work.

---

### Post by skymera on 2008-04-20
from the terminal run

sudo nvidia-xconfig

that should adjust your Xorg.conf for the Nvidia driver then it should allow Compiz.
If not, im puzzled =\

---

### Post by Sef on 2008-04-20
Read [Forlong's blog]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#") to get compiz-fusion working.

---

