---
title: "help install compiz"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2007-01-03
plz, if someone could help me i would appreciate it , because i'm trying to install compiz for 3 months now and i just can't get it...
first, my config:   intel p IV 3.0 GHz, graphic card Nvidia Gforce FX 5200, 512 Mb RAM
i am an Edgy user.
i know i have to install the Nvidia Beta driver. i downloaded it from nvidia site, but when reset the X server and try to install it it says that my kernel version is not known and can't be downloaded from tftp... i understand i have to install kernel headers...how do i do that?

> 
uname -r
2.6.17-10-generic


---

### Post by bluefrog on 2007-01-03
sudo apt-get install linux-headers-`uname -r` build-essential

after that you should be able to install your nividia drivers from the .run file

James

---

### Post by phildacey on 2007-01-03
Or you could try tseliots envy program. It installs the nvidia drivers automatically and it worked a treat for me. 

[Click here for a short guide to using the program]("http://tuxicity.wordpress.com/2006/12/22/install-the-latest-nvidia-driver-with-envy-in-kubuntu/")

---

