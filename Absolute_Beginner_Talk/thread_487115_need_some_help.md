---
title: "need some help"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2007-06-28
I've looked at the howto and on the forum as much as I can but I cannot seem to get my x1900 to work in the right resolution. I've installed the drivers and done almost every option on the how to but it does not seem to want to display in 1680 x 1050. It shows up when I config it in auto detect, and I've done the ati fix but I cannot seem to get it correct. I'm most likely missing something simple. Can you help?


theking@OptimusPrimeTheSecond:~$ aticonfig --initial --input=/etc/X11/xorg.conf
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
theking@OptimusPrimeTheSecond:~$ sudo aticonfig --initial --input=/etc/X11/xorg.conf
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
theking@OptimusPrimeTheSecond:~$ sudo aticonfig --resolution=Screen0,1680x1050,1600x1200,1280x1024
Error: Section # expected
aticonfig: parsing the command-line failed.
theking@OptimusPrimeTheSecond:~$ sudo aticonfig --resolution=Screen0,1680x1050,1600x1200,1280x1024
Error: Section # expected
aticonfig: parsing the command-line failed.
theking@OptimusPrimeTheSecond:~$ sudo aticonfig --resolution=Screen,1680x1050,1600x1200,1280x1024
Error: Section # expected
aticonfig: parsing the command-line failed.
theking@OptimusPrimeTheSecond:~$  aticonfig --resolution=Screen,1680x1050,1600x1200,1280x1024
Error: Section # expected
aticonfig: parsing the command-line failed.

---

### Post by toasty_ghosty on 2007-06-28
I just noticed something as well. The desktop effects wont work as well. help?

---

### Post by marpstar on 2007-06-28
I had a similar problem with my x800PRO card.  All I have to do was go through the xorg reconfigure, which you can do by typing into the terminal:  
```
sudo dpkg-reconfgure xserver-xorg
```

It took me awhile to play with those settings but I did get it to work.  After I configured it, I restarted the xserver (ctrl+alt+bkspace) and it came up at the correct resolution... it's worth a shot.  The problem I had was that it was not correctly detecting the monitor.  Play around with the driver, monitor, and resolution settings and you may have some luck, I did...

---

### Post by bigken on 2007-06-28
sudo dpkg-reconfgure -phigh xserver-xorg 

this only lets you select your driver and resolutions use the space bar to select

---

### Post by toasty_ghosty on 2007-06-28
thank you. I now actully have my full resolution. Now why won't my desktop effects work...

---

