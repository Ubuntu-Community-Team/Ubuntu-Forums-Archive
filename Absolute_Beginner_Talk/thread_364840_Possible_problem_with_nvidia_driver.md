---
title: "Possible problem with nvidia driver"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-02-18
I think that there may be a possible problem wiht the nvidia driver...
I installed it with the instructions on the ubuntu wiki for Drapper Drake. I installed it with 
sudo apt-get install nvidia-glx nvidia-kernel-common but had to enable it by using 
sudo gedit /etc/X11/xorg.conf
and changing the "nv" value to "nvidia" as per [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)
However, now on shut down, or restart the screen is blank and does not show the shut down progress from before....
does anyone know how I can fix this?

---

### Post by annda on 2007-02-18
does your system still work properly? can you log in? or do you only miss the shut-down messages?

---

### Post by old_geekster on 2007-02-18
> **noorez said:**
> I think that there may be a possible problem wiht the nvidia driver...
I installed it with the instructions on the ubuntu wiki for Drapper Drake. I installed it with 
sudo apt-get install nvidia-glx nvidia-kernel-common but had to enable it by using 
sudo gedit /etc/X11/xorg.conf
and changing the "nv" value to "nvidia" as per [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)
However, now on shut down, or restart the screen is blank and does not show the shut down progress from before....
does anyone know how I can fix this?
The guide that you used is good, but here is a guide that will help you install the latest nVidia drivers from their website:

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=install+latest+nvidia+drivers)

I have used it several times and it works great!

You will want to write down the instructions when he suggests it, because you will go to a command line for the last two items.

p.s. Be sure to remove the drivers that you already have installed when he instructs you to do so.  Otherwise, you will have a major problem.

---

### Post by noorez on 2007-02-22
I have installed the driver according to the instructions that you specified and everything appears to be working excellent. However, I checked up on my laptop modal and found it has a 
"NVIDA ® GeForce ™ Go 7600 256 MB graphics processor." I was wondering if the driver I installed is fully compatible with my graphics card.

---

