---
title: "Resolution Problem"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by mariano.pelizzari on 2007-10-07
I manage to install ubuntu through a pinfull 800x600 resolution. I have a ViewSonic VA1703w and a gforce FX5500, both of them support 1440x900 witch is the resolution that I want. I was told that this problem could be fixed installing the nvidia driver through envy, so i did it. Know I have only 640x480.

What should I do to get 1440x900.

---

### Post by alienexplorers on 2007-10-07
Did you remove the old nvidia driver before installing the new driver.  Have heard of problems happening when this is not done.

---

### Post by n3tfury on 2007-10-07
> **mariano.pelizzari said:**
> I manage to install ubuntu through a pinfull 800x600 resolution. I have a ViewSonic VA1703w and a gforce FX5500, both of them support 1440x900 witch is the resolution that I want. I was told that this problem could be fixed installing the nvidia driver through envy, so i did it. Know I have only 640x480.

What should I do to get 1440x900.

you probably need to take a look and add that resolution in you xorg.conf file.

---

### Post by alienexplorers on 2007-10-07
Since you have a nvidia card did you try > gksudo nvidia-settings to set the correct resolution.

---

### Post by mariano.pelizzari on 2007-10-07
Problem solved I used dpkg-reconfigure xserver-xorg and it is working

---

### Post by n3tfury on 2007-10-07
> **mariano.pelizzari said:**
> Problem solved I used dpkg-reconfigure xserver-xorg and it is working

mark this thread as solved please.

---

