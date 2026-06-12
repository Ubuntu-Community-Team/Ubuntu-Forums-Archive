---
title: "I'm confused :#"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by levigruber on 2007-01-25
I have an ongoing issue with Ubuntu and the resolution for my Viewsonic VE710B
LCD display. I have (sigh) installed Ubuntu no less than four times on my p3 600 asus p3bf
with 512 mb of ram. I went looking again today to find how to increase screen resolution
to 1280x1024 from 1024x768 (no higher res is listed). On forums I found posting which
advised I

levi@mondrian:~$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
Password:
levi@mondrian:~$ sudo dpkg-reconfigure -phigh xserver-xorg
md5sum: /etc/X11/xorg.conf: No such file or directory
levi@mondrian:~$

I mean I backed up and tried to reconfigure my xorg.conf and it does not seem to exist.

what's going on?

Thanks-

Levi:confused:

---

### Post by aysiu on 2007-01-25
You renamed it to xorg.conf.bak

You should copy instead of move: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` When you're asked for the monitor sync ranges, make sure to select 30-80 for horizontal and 50-85 for vertical. I'm basing those numbers off [this page](http://www.viewsonic.com/support/desktopdisplays/lcddisplays/e2series/ve710b/index.htm). Is that your monitor model?

---

### Post by lingnoi on 2007-01-25
Heres my guide on laptop annoyances but it says how to [fix screen resolutions]("http://www.ubuntuforums.org/showthread.php?t=295942")  too. 

Hope this helps :D

---

### Post by 3rdalbum on 2007-01-25
So you would do:

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

to fix the incorrect first command. Then do your sudo dpkg-reconfigure step.

---

### Post by erlyrisa on 2007-01-25
Type

you@shell:  man xorg.conf

you should find helpful information on how to configure ur monitor and Graphics device.

some pionts of interest you should be looking at in the help file...

mode / modes and modeline  and default

-just change your modes line for your monitor

-if its a crt and the pic looks wrong (ie wrong refresh )...

run XvidTune in a resolution that already works. (X server has tobe running)


hope this helps (PS there should be some back dated Posts that already explain alot of the nuances of Linux and User screen configuration)

PPS - there is a whole boat load of other things you could do (like flipping your monitor, or veiwing it mirrored - looks really strange and is great way to make a large screen TV - just watch your monitor on the bent mirror.)

---

