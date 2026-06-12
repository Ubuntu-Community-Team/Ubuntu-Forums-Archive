---
title: "Properly installing latest Nvidia driver (Geforce 8600GTS)"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by pencil86 on 2007-08-25
I have a Geforce 8600GTS video card and I'm trying to install the latest nvidia driver AND achieve dual screen view.

I tried using 
sudo aptitude install nvidia-glx-new
It works BUT windows move/resize slowly which means that the driver may not be used by ubuntu???


I tried manually installing the LATEST driver from NVidia site....it installs fine but when I reboot...xserver cannot start up...it gives an error saying the nvidia driver kernnel is different from the linux kernnel etc.


What is the proper way to install the driver? I just want most, all if possible, features of my Geforce 8600GTS card and dualview.

---

### Post by r4ik on 2007-08-26
Try Envy that should work,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by pencil86 on 2007-08-26
Thanks but I don't want to use Envy.

How do I manually install the NVidia driver from the NVidia website? Each time I install it and restart, xserver cannot start and complains that the nvidia driver kernel version is different from the linux kernel version.

If I try to install it using apt-get install nvidia-glx-new....it says the installation is sucessful...but the driver isn't even used because everything is "slow rendered".


Everything works if I use Envy to install the driver BUT what is envy doing that I'm not doing??????

BTW, If xserver fails to start this time...how do I tell it to use VGA mode (vesa driver?). I really want to get the driver from the nvidia website installed.

---

### Post by pencil86 on 2007-08-26
Uh Oh.....I just checked this site [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

> If your card does not appear in this [WWW] list of cards known by Ubuntu 7.04 NVIDIA binary drivers (e.g. the 8600GT is not present) then there is no Ubuntu 7.04 supported binary driver (for unsupported workarounds try the links in See Also).

My card is a 8600GTS...does this mean it will not work? How come Envy fixes the problem then if it is unsupported?

---

### Post by Perfect Storm on 2007-08-26
Envy is not supported. It's a 3rd party project which allow you to install the latest Nvidia driver. Every 6 months a new version of Ubuntu is released which have the "allmost newest" applications/software etc. (but tested, bug fixing etc.) that you can get through apt-get/aptitude/synaptic.

To manually install the nvidia drivers;

Download the latest driver to your **Desktop**


```
sudo nano /etc/default/linux-restricted-modules-common
```

edit: DISABLED_MODULES="" to DISABLED_MODULES="nv"

<ctrl>+<o> (save)
<ctrl>+<x> (exit)

```
cd ~/Desktop
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop **(This wil take you out of X and into clean commandline, so print it out)**
sudo sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run
sudo /etc/init.d/gdm start
```


If it fails and you'll be in CLI you do:
```
sudo nano /etc/X11/xorg.conf
```

go to **Section "Device"** and change **    Driver         "nvidia"** to **    Driver         "vesa"**

---

