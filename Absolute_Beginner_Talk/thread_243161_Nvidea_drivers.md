---
title: "Nvidea drivers"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by That Guy X on 2006-08-24
Hi,im new to ubuntu and i have an intergrated Nvidea Geforce 6100 graphics card.I can tell ubuntus not useing it because games are very sluggish and windows leave trails.Does anyone know were i can find the driver and how to install it? :confused: 




 Thanks in advance,
                    Steve

---

### Post by meng on 2006-08-24
Try
sudo aptitude install nvidia-glx
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by baldy1324 on 2006-08-24
this is b/c ubuntu does not defaultly use drivers dont have 3d acceleration. to get these drivers do the following. type ```
sudo aptitude install linux-restricted-modules-`uname -r`
```this will install a lot of non-open-source drivers for your specific kernel. however whenever apt-get upgrade updates your kernel these drivers. so dont update your kernel. now type ```
gksudo "gedit /etc/X11/xorg.conf"
```then replace the line that says nv with nvidia (which is in the Device section.
hope this helps:)

---

### Post by Pantuflo on 2006-08-24
I think this is a very detailed guide with could help you:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

I've tried some other methods like downloading "nvidia-glx" and then modifying xorg.conf, and I only managed to broke my graphical interface.
However, that guide (following the link above) will help you more (there is a "problems section", and very detailed steps).

---

### Post by That Guy X on 2006-08-24
I tryed baldys method and replaced 'vega' with 'Nvidea' under devices.When i boot the Nvidea logo comes up and it seems to work fine:)  Thanks for the help

---

