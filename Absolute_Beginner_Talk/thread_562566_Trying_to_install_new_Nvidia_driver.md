---
title: "Trying to install new Nvidia driver"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by jaytek13 on 2007-09-28
Nvidia came out with a new driver recently. I'm trying to follow the instructions on the nvidia website to install it. Unfortunately it is giving me an error message about how X should not be running when you do install it. So, I rebooted into failsafe and did that, and it told me I needed to at least be running in init3. So, I started init3 and it booted up X again.

In other distro's it's always been fairly easy to just reboot into console mode, but I can't seem to find an easy way to do it on ubuntu. Is there a way to do this or will I have to configure a new init?

---

### Post by Pumalite on 2007-09-28
Ctrl+Alt+F2
login with your username
your password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIA-Linux-x86 blah, blah, blah
Accept the license
Let the driver compile your modules
Let the driver reconfigure your xorg file
sudo /etc/init.d/gdm start
startx if need be

---

### Post by uglykigjoe on 2007-09-28
i used this thread instead 

[http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

:guitar:

---

