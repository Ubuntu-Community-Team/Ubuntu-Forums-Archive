---
title: "Monitor doesn't work correctly on boot up screens"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by dean.s.wood on 2007-01-07
Hi, 

Have been meaning to try and fix this for a while but have only just got the time. On boot up the screen does not display properly. The screen is shifted to the left and wrapped around again on the right so the screen looks very strange. It also does this if I press Ctrl-Alt-F1-6 to get a terminal screen without X running.

I am using a Fujitsu siemens laptop and the screen hardware is a VIA S3 Unichrome Pro VGA Adapter. I am fairly certain I need some settings in Grub but am not sure where to start.

Any advice gratefully recieved.

Thanks 

Dean

---

### Post by kepos on 2007-01-07
when using high resolutions, and you switch to lower ones your monitor may require to set up geometry again. not shure about laptops, but it sometimes happens on classical monitors.

---

### Post by mnhercules84 on 2007-01-26
> **dean.s.wood said:**
> Hi, 

Have been meaning to try and fix this for a while but have only just got the time. On boot up the screen does not display properly. The screen is shifted to the left and wrapped around again on the right so the screen looks very strange. It also does this if I press Ctrl-Alt-F1-6 to get a terminal screen without X running.

I am using a Fujitsu siemens laptop and the screen hardware is a VIA S3 Unichrome Pro VGA Adapter. I am fairly certain I need some settings in Grub but am not sure where to start.

Any advice gratefully recieved.

Thanks 

Dean

I have the same problem. Any solutions? I also have Fujitsu Siemens and the same graphic adapter.
And can somebody help me to set screen resolution 1280x800 because I don't have to chose it?
I am new with UBUNTU. Only 4 hours :-)
Tnx in advance.

---

### Post by teaker1s on 2007-01-26
panel click applications -accessories-terminal 

[COLOR="Red"]Sudo dpkg-reconfigure xserver-xorg[/COLOR]

---

### Post by mnhercules84 on 2007-01-27
I have tried that. And it s not working :(

---

### Post by teaker1s on 2007-01-30
in terminal
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

will allow reconfiguring of xserver and allow you to tell xserver the resolutions your adapter can display

---

### Post by mnhercules84 on 2007-01-30
I add  my screen resolution 1280 x 800 in /etc/X11/xorg.conf
but still my boot up screen is moved to the left or right whatever :(

---

### Post by teaker1s on 2007-01-31
sorry I scanned the thread and miss read, 
try searching forums it could be resolution related to grub / usplash settings as others have complained about usplash corruption

---

