---
title: "[SOLVED] ATI card with 7.10"
date: 2007-10-19
forum: Apple Intel Users
---

### Post by eodchop on 2007-10-19
Has anyone had any luck getting their ATI cards working in their macbook pros under 7.10. I have installed the restricted driver but Compiz Fusion is not working. After i installed the restricted driver i had to reboot. Upon reboot, i was in a very low screen resolution. I ran sudo dpkg-reconfigure xserver-xorg. I set the proper resolution but now i get an error that says the composite extension is not available when i attempt to enable them.

Thanks 


Ryan

---

### Post by mcdull2k on 2007-10-19
you still need XGL to get compiz to work until ATI driver 8.42 comes (hopefully it works)

apt-get install xserver-xgl

---

### Post by cyberdork33 on 2007-10-19
> **mcdull2k said:**
> you still need XGL to get compiz to work until ATI driver 8.42 comes (hopefully it works)

apt-get install xserver-xgl

And restart again...

---

### Post by clayboy on 2007-10-19
cyber i followed you the instructions you sent me and no all i get is a black screen when trying to boot any suggestions to help 

setup 
2.8 alu imac
ati hd2600
Gusty 7.10 
attempting to use 8.41.7

---

### Post by eodchop on 2007-10-19
I thought this was all preinstalled? Compiz/fusion/xgl? Are there specific packages i need to install.

---

### Post by eodchop on 2007-10-19
> **clayboy said:**
> cyber i followed you the instructions you sent me and no all i get is a black screen when trying to boot any suggestions to help 

setup 
2.8 alu imac
ati hd2600
Gusty 7.10 
attempting to use 8.41.7

Have you gotten it to working yet? I am afraid to install the suggested package and brick my shiny new install.

---

### Post by clayboy on 2007-10-19
no go on the fglrx driver i cant get that thing install im following directions and **** aint happening but a black screen on boot up. did you get the fglrx drivers installed

---

### Post by eodchop on 2007-10-19
> **clayboy said:**
> no go on the fglrx driver i cant get that thing install im following directions and **** aint happening but a black screen on boot up. did e you get the fglrx drivers installed

Yes i took a chance and installed the driver and also installed the xgl-xserver package and it is actually working!! Now if i can just figure out this damn synaptics touchpad sesitivity and get it to right click i will be bug free. Your card may not be compatible with the ATI driver since it is a rather new card. I have heard ATI is open sourcing their drivers and working the FOSS community to make better drivers. Just havent seen a road map.

---

### Post by cyberdork33 on 2007-10-19
> **eodchop said:**
> I thought this was all preinstalled? Compiz/fusion/xgl? Are there specific packages i need to install.
XGL is not already installed as it is only required by fglrx.

clayboy, please do stick to one thread with your problem as it is confusing when you post in another about something different. I will post in your earlier thread.

---

### Post by eodchop on 2007-10-19
Thanks for the help. I learned something today. How do I mark this as solved?

---

### Post by cyberdork33 on 2007-10-19
> **eodchop said:**
> Thanks for the help. I learned something today. How do I mark this as solved?
In the "Thread Tools" menu at the top.

---

