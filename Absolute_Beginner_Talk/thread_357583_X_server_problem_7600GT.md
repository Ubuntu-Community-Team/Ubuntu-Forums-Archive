---
title: "X server problem 7600GT"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by syriusblack on 2007-02-09
So like alot of people apperantly I am having the "X server (EE) no device detected" problem, 

I read the wiki and it looks like my drivers arent supported on ubuntu 5.10.  Are the 7600GT drivers supported in a later version?  if not how can I fix this through command prompt....er i mean shell.

thanks guys, ubuntu is great and so is the community

---

### Post by riven0 on 2007-02-09
When you get to the terminal, log in and type:

> sudo apt-get install nvidia-glx

Now, open your xorg.conf file and edit the Driver section:

> sudo nano -w /etc/X11/xorg.conf

Scroll down till you get to this section: 

> 
Section "Device"
Driver "nv" 

and change to:

> Driver "nvidia"

Now reboot.

---

