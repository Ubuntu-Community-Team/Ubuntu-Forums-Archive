---
title: "System freeze, failed to reboot"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by leneumann on 2008-02-28
I have installed Ubuntu 7.1 on a X64 and experienced some of the freezing problems after sometime as reported in the thread:

[http://ubuntuforums.org/showthread.php?t=587905&highlight=freeze]("http://ubuntuforums.org/showthread.php?t=587905&highlight=freeze")

This seems to be my problem since I do have a NVidia GF8600 and dual core. However, I did reboot the system and after selecting Ubuntu at grub, I get a blank screen and the system does not come up. If I reboot again and choose windows, I have no problems and the systems runs fine. 

I believe i have to update the drivers, but how do I get to boot and do so? Do I have to use the live CD? How do I go about it.

Any help is appreciated

Cheers

Luis

---

### Post by jucas_lo on 2008-02-28
try booting in failsafe mode and reinstalling the nvidia driver.....I don't have an Nvidia card so I can't tell you exactly how to do it.....but from what I've seen you should do ```
sudo apt-get install nvidia-glx
``` then make sure that you're using the nvidia kernel in your /etc/X11/xorg.conf file...to do that just ```
sudo nano /etc/X11/xorg.conf
``` then look for the part that says driver and check that it says nvidia and not nv....if it says "nv" change it to "nvidia" and reboot again....

hope that helps

PD to install the driver you should be able to connect to the internet....when in failsafe mode....if you can't try to download the packages from your Windows or other operating system and then install the deb package with dpkg -i (/path / to /package)

---

