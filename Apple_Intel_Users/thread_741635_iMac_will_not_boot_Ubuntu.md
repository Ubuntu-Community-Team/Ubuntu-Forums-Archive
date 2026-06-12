---
title: "iMac will not boot Ubuntu"
date: 2008-03-31
forum: Apple Intel Users
---

### Post by dh122 on 2008-03-31
Sorry if this question is already answered, but I cannot find a solution anywhere.

I have installed UbuntuStudio 7.10 on my iMac. (Intel Core Duo 1.83 Gz. 17in. running Mac OS X 10.4.11 all updated) The installation goes smoothly, but when I attempt to boot into Ubuntu, It tells me that the display has reset 6 times in the last 90 seconds and something bad is happening. I have also tried this with a normal Ubuntu live cd, same problem. Does anyone have a solution?

---

### Post by cyberdork33 on 2008-04-01
> **dh122 said:**
> Sorry if this question is already answered, but I cannot find a solution anywhere.

I have installed UbuntuStudio 7.10 on my iMac. (Intel Core Duo 1.83 Gz. 17in. running Mac OS X 10.4.11 all updated) The installation goes smoothly, but when I attempt to boot into Ubuntu, It tells me that the display has reset 6 times in the last 90 seconds and something bad is happening. I have also tried this with a normal Ubuntu live cd, same problem. Does anyone have a solution?
you need to install the proprietary ATI driver. changing the driver to "vesa" in /etc/X11/xorg.conf should get you to the point where you can use envy to install the latest ATI driver with Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by dh122 on 2008-04-01
Sounds good, but how do I access the /etc/X11/xorg.conf. file? Is that a file in Ubuntu, because I cannot even enter Ubuntu. I looked in OS X, but that file did not exist. Could I access it through rEFIt's terminal window?

---

### Post by cyberdork33 on 2008-04-01
> **dh122 said:**
> Sounds good, but how do I access the /etc/X11/xorg.conf. file? Is that a file in Ubuntu, because I cannot even enter Ubuntu. I looked in OS X, but that file did not exist. Could I access it through rEFIt's terminal window?
[LIST]
[*] After Xorg fails, go to a terminal via CTRL+ALT+F1
[*] Login
[*] ```
sudo nano /etc/X11/Xorg.conf
```
[*]Make changes, save, reboot[/LIST]

---

### Post by dh122 on 2008-04-01
Thanks for the help, I got to the file alright. Just one problem: the driver for the video card is already  "vesa". Is it something else (like the display) that needs the vesa driver, or do I have a different problem?

---

