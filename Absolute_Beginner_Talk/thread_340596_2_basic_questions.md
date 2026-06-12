---
title: "2 basic questions"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by bala.variyam on 2007-01-17
Hi,

I am very new to Ubuntu and I have 2 (perhaps) basic questions:

1. My monitor can take resolutions upto [COLOR="Blue"]**1600x1200**[/COLOR], while in the System->Preferences->Screen Resolution only three settings are listed: 1024x768, 800x600 and 640x480.  Only refresh rate listed is "60 Hz". I have tried the following things:
a) manually edit the [COLOR="DarkRed"]**/etc/X11/xorg.conf**[/COLOR] file to include "1600x1200"
b) **sudo dpkg-reconfigure -phigh xserver-xorg** (which i saw in another thread in one of the web forums)

either of this did not work.  can someone help?

2. the Firefox version that got pre-installed with the ubuntu distro cd is 1.5.0.8.  I know that the latest firefox version is 2.0.0.1.  when i go to applications->add/remove, the version of firefox available for upgrade is listed as 1.5.0.9.  how come?  how do i get the latest version?

thanks a ton,
cheers,
bala

---

### Post by taurus on 2007-01-17
1.  You probably need to install a driver for your graphic card first!  What is it anyway?

2.  [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by bala.variyam on 2007-01-17
1. The graphic card is "NVIDIA Quadro NVS 285 128MB".  How do I determine what driver I have and what driver I need?

2. I will try this out for firefox installation.

thanks,
bala

---

### Post by taurus on 2007-01-17
You can look in /etc/X11/xorg.conf to see what "Driver" you use.  It's probably either vesa or nv.

You need the nvidia driver though.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

