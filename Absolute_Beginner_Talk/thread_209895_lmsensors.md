---
title: "lmsensors"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-07-05
Trying to get a few gdesk appelets working..I tried searching thru synaptic for lmsensor but nothing shows up? Is this already installed or must i obtain the source of it then build it and compile it for ubuntu and if so where to get it from?

---

### Post by ayates on 2006-07-05
Try lm-sensors.

---

### Post by scxtt on 2006-07-05
if you do get lm-sensors installed and running and it also works w/ gdesklets - let me know - i have a fully functioning lm-sensors, which works w/ gnome-sensors-applet but lm-sensors+gdesklets aren't working well as a team ...

---

### Post by lime4x4 on 2006-07-05
ok i installed lm-sensor now how do i start or configure it??
I know at the command line lm-sensor  does nothing just gives an error

---

### Post by scxtt on 2006-07-05
sensors-detect will do most of the work ...

---

### Post by lime4x4 on 2006-07-05
john@ubuntu:~$ sensors-detect
No i2c device files found. Use prog/mkdev/mkdev.sh to create them.

---

### Post by lime4x4 on 2006-07-05
well i did find the i2c source files just can't use them...lol

These are the installation instructions for the i2c package.
This package is ONLY for 2.4 kernels 2.4.10 or later!

FOR 2.5/2.6 KERNELS, do not attempt to compile this package.
    Use the drivers already in the 2.5/2.6 kernel tree.

---

### Post by mcduck on 2006-07-06
You should't need to compile anything for lm-sensors. TTry following this howto: [http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors]("http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors")

---

