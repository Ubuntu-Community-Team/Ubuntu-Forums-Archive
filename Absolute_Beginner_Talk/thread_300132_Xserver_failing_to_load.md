---
title: "Xserver failing to load"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by lucid on 2006-11-15
Hi, about three months ago I was unable to boot Dapper. Instead I got a blue screen with a grey box saying that Xserver was unable to load, overlaid with a text login prompt. 

The only change I'd made in the previous session to the system was to download the latest updates. 

Any way I can fix this or do I need to reinstall? I'd appreciate some advice. :)

---

### Post by frodon on 2006-11-15
Boot in recovery mode and run these command :```
sudo apt-get update
sudo apt-get upgrade
```This update was broken at the time but has been fixed several day after, so a simple upgrade of the packages should fix it.

---

### Post by jd65pl on 2006-11-15
Try booting in recovery mode, which is selected from the grub boot menu.

Then do
```
 dpkg-reconfigure xserver-xorg
```Reconfigure the X server with the appropriate settings. If your driver is the cause you may wish to use the driver "vesa" to enable you to login graphically to find a resolution to your problem.

---

### Post by junglepeanut on 2006-11-15
Probably you have an ati or nvidia card and did not have the driver yet so needed to choose something like vesa when you reconfigure xserver to get it to work and then download the drivers.

Sorry, I forgot to refresh before posting it looks like it has been answered.

---

