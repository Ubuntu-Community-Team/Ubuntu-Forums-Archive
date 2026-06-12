---
title: "Nvidia + xserver failure"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by LordxAngel on 2007-07-11
Hello i had two issues when i installed Ubuntu feisty on my machine , one was the winmodem and still gives me a headache to get it to work but it does connect after fighting with it ( i don't know what Linux ubuntu devlopers are doing regarding that issue because it's the end of 2007 and it's silly that major issues like that are not fixed ) , second issue is the graphic card drivers i downlaoded the Nvidia 100.14.11 Nvidia driver and installed the Nvidia-glx-dev using synpatic finished installing the driver and restarted the computer then the Xserver crashed on me i used the sudo dpkg-reconfigure xserver-xorg to get the GUI to work again but the Nvidia driver has been disabled , is there a real solution for this problem or i am gonna have to wait for a future releases from ubuntu to get my Nvidia working ?

---

### Post by PgR on 2007-07-11
So you're running the nv driver not nvidia? 

I've had similar problems with nvidia drivers before. In the past I've added 

DISABLED_MODULES="nv" 

to the bottom of /etc/default/linux-restricted-modules-common. That seemed to work until I upgraded either linux-restricted... or nvidia's drivers.

This latest time I just uninstalled linux-restricted-modules-common.

---

### Post by MementoMori on 2007-07-11
I've had the same problem arise with the same drivers. It was a routine install, even, and now my X is busted.

[http://ubuntuforums.org/showthread.php?t=495464](http://ubuntuforums.org/showthread.php?t=495464)

---

### Post by LordxAngel on 2007-07-11
actually i am running it on vesa driver i tried the NV driver but it didn't work for me and gave me the same error , after enabling the vesa driver i tried different methods but with no luck and i posted this thread in this forum hoping that the developers on ubuntu project will explain what is wrong with Ubuntu and what causes this issue , if there is a solution for it or are they even working on it

---

