---
title: "[SOLVED] Ok now what?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2008-02-22
How do you repair Xorg on a dual boot 7.04 and XP install from the live cd, seems the only way I can access the Linux system at this point, stalls then dies during start-up after nvidia driver uograde.:confused:

---

### Post by Trail on 2008-02-22
You don't need a live cd. Boot ubuntu until "it dies" then hit control-alt-f2, which will allow you to login through a terminal. Type:

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
(and follow the guide, make sure you select "nv" and not any resolutions your monitor does not support)
after that, either reboot, or type /etc/init.d/gdm start

---

### Post by J11Gyro on 2008-02-22
Ok did that and I end up with blinking cursor at top left of screen:(

---

### Post by J11Gyro on 2008-02-22
Ok finally got the thing back to desktop but am unable to change monitor type or any settings in nvidia control panel, what now?

---

### Post by LeAstrale on 2008-02-22
are you using restricted drivers management for the driver or are you using the nvidia.com driver ?

and also could you pls post which graphics card you have? (lspci | grep vga)

and the display and screen parts of your xorg.conf pls

/Astral-1

---

### Post by J11Gyro on 2008-02-22
Problem solved, went through Envy and un-installed current driver and installed latest, which is not always best, and got everything working as should. Even got control panel back. Thanks for the help cause I am really brain dead sometimes, I guess memory is going :)

---

