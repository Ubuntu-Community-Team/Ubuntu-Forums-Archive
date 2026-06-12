---
title: "Kubuntu / Ubuntu and ATI Drivers ???"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by menawollas on 2006-06-27
Hi,

I installed Ubuntu, and followed the ATI driver howto for my Radeon 9600, and everything worked fine. I can set a refresh rate of 85Hz at 1024*768,

I then installed KDE, and it didn't like it. Basically, it was at 60Hz, I changed it to 85, and on restarting, it was set to 640*480@60Hz. And I couldn't change it. Changing the session to Gnome it was just the same.

So I installed Kubuntu. And after installing the ATI drivers, and rebooting, it forced it to 640*480@60Hz. 

Whats going on? 

Why is KDE not happy with the Radeon setting when Gnome is.

I am totally confused????

---

### Post by shoot2kill on 2006-06-27
sounds like you havnt got all of the correct screen resolutiuons set in your xorg.conf

post your xorg details here

> gedit /etc/X11/xorg.conf

---

### Post by bruce89 on 2006-06-27
```
sudo dpkg-reconfigure xserver-xorg
``` and select the fglrx driver.

---

### Post by menawollas on 2006-06-27
The Xorg.conf gets stupid](*,)  I don't have it at the moment due to a reinstall, but it seems to insert multiple screen and device sections.

At present, I have selected (in Kubuntu) the correct monitor and the  Radeon card, and it lets me set up 85Hz. (it says its fglrx)

However, when it goes wrong is when I do the 

sudo apt-get install xorg-driver-fglrx

to get the new driver. That when on resetting and rebooting, things get set back to 640*480@60Hz. A modeline gets created to that effect as well.

---

