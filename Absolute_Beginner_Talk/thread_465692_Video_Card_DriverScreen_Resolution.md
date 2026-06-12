---
title: "Video Card Driver/Screen Resolution"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Andrewz on 2007-06-06
Hi there, I just installed ubuntu and have been trying to figure out how I might configure my video card, do I need to install a driver? I cannot view my optimal resolution right now which is 1680x1050, the highest it lets me go is 1162x864. Any help would be appreciated, thanks.:p

---

### Post by Crafty Kisses on 2007-06-06
> **Andrewz said:**
> Hi there, I just installed ubuntu and have been trying to figure out how I might configure my video card, do I need to install a driver? I cannot view my optimal resolution right now which is 1680x1050, the highest it lets me go is 1162x864. Any help would be appreciated, thanks.:p

If you're using edgy you can install your drivers manually, but if you have Ubuntu 7.04 and have a nVidia card, System > Administration > Restricted Devices Manager

Enable Driver

Apply Changes 

You can also do it the manual way, by doing the following in the terminal.

```
sudo gedit /etc/apt/sources.list
```
Then go into your architecture (Xorg.conf file) and add one of these lines, which ever one applies to you.
```
deb http://www.albertomilone.com/drivers/edgy/latest/32bit
```
```
deb http://www.albertomilone.com/drivers/edgy/latest/64bit
```
If you don't want to go through all that, you can download a script  called "Envy" which installs the drivers for you at:
[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

