---
title: "NVIDIA GeForce 7600 GT installation problem"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Racer_D on 2008-02-27
Hi guys... i m hving problem installing NVIDIA GeForce 7600 GT on my desktop PC. when i go to restricted drivers window, i c NVIDIA accelerated graphics driver (latest cards) under driver option. The enable check-mark is not selected and the status is "not in use". when i checked enable check box, a window prompt up saying
Enable the driver?
NVIDIA accelerated graphics driver (latest cards)
The driver is required ......

when i clicked enable driver button, it says

"The software source for the package nvidia-glx-new is not enabled.

any comments?????

---

### Post by glennric on 2008-02-27
Make sure that the gutsy-updates/restricted and/or gutsy/restricted repositories are enabled.  To do this go to System->Administration->Software Sources

---

### Post by Racer_D on 2008-02-27
ya i enabled it, but hving same problem. i guess it won't run as i m also hv trouble with my wireless network adapter (Linksys adapter, Wireless-G (802.11g) WMP54GX4 )... :(

---

### Post by incen on 2008-02-28
I have the same graphic card. Although I can check that item without no problem. However, after checking it, it required a reboot and then it totally killed my computer. I cannot boot regularly anymore. Then, I go to download the latest driver Nvidia has and this post helps me:
[http://ubuntuforums.org/showthread.php?t=692827](http://ubuntuforums.org/showthread.php?t=692827)
I mainly followed what PmDematagoda said. Kill X-server and installed the latest driver and then back to X-server again. ^^

---

### Post by Racer_D on 2008-02-28
tried the second part, which is

2. Download the Nvidia driver:-

Code:wget [http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.07/NVIDIA-Linux-x86-169.07-pkg1.run)

it gave me error ERROR: nvidia-installer must be run as root

---

### Post by glennric on 2008-02-28
So does that computer have internet connection at all?  You will not be able to install packages from the repositories if you don't have internet connection.  

If you want to download the drivers from NVidia and install them, type
```
sudo /etc/init.d/gdm stop
```
Change to the directory where you dloaded the driver and type
```
sudo sh NVIDIA-Linux-*.run
```
and follow the instructions of the installer.  Make sure that you have the linux-headers package installed, and make sure that you do not have the restricted-modules installed.  Since you have wireless, I am guessing you may need the restricted drivers, which means this method of installing the drivers is not really an option for you.

---

### Post by incen on 2008-02-29
Sorry that I didn't see your reply. You may need to change the link a little bit, depending on which Ubuntu version you have. If you have Ubuntu 64 bit, you should change the link to
```
http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run

```

---

### Post by Rabindranath on 2008-02-29
I think installing the driver through 'envy' is more easier and better. It installs the driver from the nvidia website and it is very easy.

---

### Post by philinux on 2008-02-29
ENVY site [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

