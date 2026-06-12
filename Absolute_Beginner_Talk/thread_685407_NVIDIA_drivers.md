---
title: "NVIDIA drivers"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by fusionenvy on 2008-02-02
I have tried ENVY i have tried manual install  ... nothing works ... I get nothing... no xserver ... nothing but errors. 

Everything was fine 8 hours ago... thats how long i have been trying to fix this
but when i went to run Portal a dialog came up alerting me that my driver was out of date

so i tried to update the driver.

results 8 hours of crazed attempts to upgrade or RESTORE the old driver

Ive got NOTHING but a stock driver that does not even do Q3

HELP

Again i have tried Envy ... I have tried all forms and fashions of driver install and end up with the same results.

are there things i dont have installed that are causing the issues?


HELP!!

---

### Post by violin on 2008-02-02
I dont know whether this will help but have you tried automatix 2?

---

### Post by fusionenvy on 2008-02-02
yah....


um 

where can i download that:(

---

### Post by Malta paul on 2008-02-02
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by Nythain on 2008-02-02
```

sudo aptitude install nvidia-glx (or nvidia-glx-new or nvidia-glx-legacy depending no card)
sudo dpkg-reconfigure -phigh xserver-xorg

```
making sure to select the nvidia driver and not nv driver????

---

### Post by overdrank on 2008-02-02
> **fusionenvy said:**
> yah....


um 

where can i download that:(

Hi and  What is the model of the graphics card and what Nythain posted is good advice.
[https://help.ubuntu.com/community/Automatix](https://help.ubuntu.com/community/Automatix)

---

### Post by Teasdale on 2008-02-02
I have an NVidia GeForce2 and I'm having similar problems. We've tried different drivers, Envy - anything we do makes it worse! It makes the computer not start past a screen with the NVidia logo. Right now we're using a generic driver that came with Ubuntu, but it's not quite right and the graphics are slow.

I'll take a look at automatix 2 and see if it looks like it might help. I'm open to any suggestions. I've had Linux (Ubuntu 7.10) for 3 days. So far, this is the only problem we've had.

---

### Post by PmDematagoda on 2008-02-02
Install the nvidia-glx-legacy package using:-
```
sudo apt-get install nvidia-glx-legacy
```
After the package is installed execute:-
```
sudo nvidia-settings --config enable
```
That should fix the problem.

---

