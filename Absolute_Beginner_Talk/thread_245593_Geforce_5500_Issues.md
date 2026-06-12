---
title: "Geforce 5500 Issues?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by brashquido on 2006-08-28
Hi All,

Just installed 6.06 and all is well, except for one small issue. I have a Panasonic S110 21" monitor that is hooked up to a dual head Nvidia Geforce 5500 8X AGP graphics card with 256MB RAM. The problem is that I am unable to increase the desktop beyond 1024x768, where my monitor supports upto 1600x1200@75Hz. At first I though it was my xorg.conf settings, so I went back through the reconfiguration process for xorg and set the correct resolution and H & V scan rates for my monitor. However I am still unable to increase the desktop even after a reboot. I'm using the video driver from my Ubuntu CD. Should I be using another driver, or am I overlooking something else that is preventing me from being able to increase my desktop size?

---

### Post by mejy on 2006-08-28
> **brashquido said:**
> Hi All,

Just installed 6.06 and all is well, except for one small issue. I have a Panasonic S110 21" monitor that is hooked up to a dual head Nvidia Geforce 5500 8X AGP graphics card with 256MB RAM. The problem is that I am unable to increase the desktop beyond 1024x768, where my monitor supports upto 1600x1200@75Hz. At first I though it was my xorg.conf settings, so I went back through the reconfiguration process for xorg and set the correct resolution and H & V scan rates for my monitor. However I am still unable to increase the desktop even after a reboot. I'm using the video driver from my Ubuntu CD. Should I be using another driver, or am I overlooking something else that is preventing me from being able to increase my desktop size?

You may want to use the official nVidia driver.  I can't guarentee this will solve your problems, but you should use it anyway if you want 3D acceleration (for XGL for example - look into it ;) ). For a simple install guide, look here: 
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

If it complains that you've modified your xorg.conf, edit it again and change the driver from nv to nvidia.

If that fails, post your xorg.conf here.

---

