---
title: "video card problem.. help plz"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by smalss on 2007-07-31
Hey everyone, just installed ubuntu. First time ever using Linux. Heard nothing but great things about it. I am not sure if my nvidia geforce go 7600 is working properly. it doesn't let me select the highest resolution that i can have. The restricted drive thing came up right away, so i went to system>administration>restricted drivers and selected the nvidia option, it installed i thought. 
Did i do it right, or am i missing something??? there is no restricted drivers icon in the top right anymore. 

I tried to search for the problem on the forum but i am just not sure which option to follow. If someone could point me in the right direction that would be sweet.

Thnx

---

### Post by amgeex on 2007-07-31
Go into synaptic and search for nvidia, the driver you have currently installed should come up. If its nvidia-glx, uninstall it and then install nvidia-glx-new, so you get a fairly recent driver. After this open un a terminal and type sudo nvidia-xconfig, and that should enable the driver, and with any luck it'll automaticlly set the proper resolution for your monitor. If this isn't the case you can edit your xorg.conf file that's located in /etc/X11/xorg.conf.

Cheers, and good luck!

---

### Post by smalss on 2007-07-31
What would i be changing in the xorg.conf file??? 

i tried the nvidia-glx-new and all that but nothing seemed to happen.

---

### Post by smalss on 2007-07-31
i found a website that says how to install nvidia card, i followed the directions, rebooted, and it didn't even boot to ubuntu.. gave me errors on a blue screen then all i could do was type in a terminal. Help.. what can i do?

---

