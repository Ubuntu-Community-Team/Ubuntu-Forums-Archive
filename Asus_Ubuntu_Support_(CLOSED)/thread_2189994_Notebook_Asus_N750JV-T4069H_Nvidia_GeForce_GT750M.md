---
title: "Notebook Asus N750JV-T4069H: Nvidia GeForce GT750M"
date: 2013-11-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by aljosa2 on 2013-11-25
Hi all,
happy with 7 months Linux experience on old HP desktop, few days ago I deleted Windows from my brand new notebook Asus N750JV-T4069H (Intel® Core™ i7-4700HQ; Bit 64; Nvidia GeForce GT750M) and installed Xubuntu 13.10. I'm not sure but it seems to me that my problem is Xubuntu bug. If this is the case, I would be very grateful if someone can communicate the problem to the development team 'cause I get lost inside the more than complicated bug reporting procedure: 


- Nvidia GeForce GT750M is not recognized 
(after many experiments with all kinds of drivers and stuff like Bumblebee, the only thing that somehow works is - "NVIDIA binary Xorg driver/kernel module and VDPAU library nvidia 319-updates/Proprietary" - but during startup some strange black screen with vertical colored lines appears instead of Nvidia logo, and later settings like brightness, contrast and other missing).

---

### Post by Toz on 2013-11-25
See [https://wiki.debian.org/InstallingDebianOn/Asus/N750JV/Jessie]("https://wiki.debian.org/InstallingDebianOn/Asus/N750JV/Jessie"). Looks like you need the 325 or greater drivers.

---

### Post by aljosa2 on 2013-11-25
thanks for reply - already tried (331.20 included)

---

### Post by aljosa2 on 2013-11-26
I have reinstalled Xubuntu once again. Don't know if it is of any importance, but in my computer ther'e no a single trace of Windows 8 (uefi/boot).
So after 


sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331 nvidia-settings-331 nvidia-prime


situation is much better now - generally speaking. Still there's no Nvidia logo durin startup, and settings like brightness and contrast missing.

---

### Post by side2k on 2013-12-05
Thanks, xorg-edgers ppa helped.  glxinfo showed that picture is rendered via GT750M GPU. But after I tried to change resolution(I have Kubuntu) and save config in nvidia-settings, screen went black. 
I rebooted just to find out that GUI is not starting anymore.
Rebooted again in text mode, analyzed the log and saw that there is "NVidia persistense daemon" failed to start. I removed /etc/X11/xorg.conf and rebooted. 
GUI is working again, but drivers are not. I tried dpkg-reconfigure, tried purging and re-installing - and still, it doesn't work.

---

