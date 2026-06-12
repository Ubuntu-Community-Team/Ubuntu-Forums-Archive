---
title: "graphics card setup"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by el_ricardo on 2006-02-13
how should i install the necessary drivers for my graphics card? i have an nvidia 6200, also howdo i get openGL working properly or will a driver update fix this or what?

---

### Post by codejunkie on 2006-02-13
[QUOTE=el_ricardo]how should i install the necessary drivers for my graphics card? i have an nvidia 6200, also howdo i get openGL working properly or will a driver update fix this or what?[/QUOTE]
what version of ubuntu are you using?

---

### Post by el_ricardo on 2006-02-13
i'm using 5.10

<edit>think i've got it actually, found the legacy drivers in the package manager and downloaded them, is there anything else i need to do after this?</edit>

---

### Post by codejunkie on 2006-02-13
download the driver for your cpu type at [www.nvidia.com](www.nvidia.com) open a terminal and enter
```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4
```
now ```
sudo apt-get remove --purge nvidia*
```
press ctrl+alt+F1 cd to the folder you downloaded the nvidia package for example: if you put it in your home dir you would use cd /home/yourusername 
now kill the xserver with ```
sudo /etc/init.d/gdm stop
```switch to the root user with ```
sudo su
```and run```
export CC=gcc-3.4
```now you install the driver with 
```
sh NVIDIA-Linux-x86-1.0-8178-pkg1.run
```
and last you have to change the driver line in your /etc/X11/xorg.conf file to nvidia with ```
sudo nano /etc/X11/xorg.conf
``` scroll down to the "Device" section and change what's listed in the "Driver" line to "nvidia" save the file by pressing ctrl+x and restart the xserver with ```
/etc/init.d/gdm restart
``` or reboot your computer.

---

### Post by codejunkie on 2006-02-13
[QUOTE=el_ricardo]i'm using 5.10

<edit>think i've got it actually, found the legacy drivers in the package manager and downloaded them, is there anything else i need to do after this?</edit>[/QUOTE]
you can't use the legacy driver with the nvidia 6200 card the legacy driver is for older nvidia cards that nvidia doesn't support any more.

---

### Post by el_ricardo on 2006-02-13
yeah it didn't seem to make a difference, i'll try the above then

---

### Post by codejunkie on 2006-02-13
[QUOTE=el_ricardo]yeah it didn't seem to make a difference, i'll try the above then[/QUOTE]
if you don't feel like going through all the steps to compile the driver from nvidia
there is an older driver in synaptic that might work on your card, but some people say that they have had problems using it on nvidia 6200 and above cards so i can't say for sure if it will work on your card you can install it with 
```
sudo apt-get install nvidia-glx nvidia-settings
```
then change the driver in the /etc/X11/xorg.conf file with 
```
sudo nvidia-glx-config enable
```

---

### Post by Gvaz on 2006-02-13
i was wondering something similar.

i have a ATI Radeon 9600 SE and i downloaded the driver from ATI.
when i install it (its a .run file), will that be enough, or is there other steps i must take?

---

### Post by el_ricardo on 2006-02-13
i managed to get to the install stage with the code above, but apparantly it needs gcc4.0 not 3.4 ... or something, theres also something wrong with my kernal apparantly, it doesn't match the one with the graphics card driver

<edit>got it working, must have made a typo earlier or something, its all installed now, cheers!</edit>

---

### Post by soonindallas on 2006-02-13
[QUOTE=Gvaz]i was wondering something similar.

i have a ATI Radeon 9600 SE and i downloaded the driver from ATI.
when i install it (its a .run file), will that be enough, or is there other steps i must take?[/QUOTE]

I advise checking that the .run file you got from the ati site has execute permissions.

As for the other steps, I followed this how-to to get my ati card working with success: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by Gvaz on 2006-02-13
thanks, i'll try that in a few hours when i get home :D

---

