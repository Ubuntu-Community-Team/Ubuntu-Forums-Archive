---
title: "Video problems on install"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by ljpm on 2006-07-14
Hi all,

I am a complete beginner so please keep all replies very simple.

I have installed 6.06 i386 on an AMD64 (heard i386 installed easier and was better than AMD64 bit version) with a Radeon ATI integrated video card and a sony (DVI) flat panel monitor. 

The screen resolution is set at 640 x 480. (this also make the installation difficult since all the windows are larger than the screen and have to be moved around)

I have tried to install the video driver according to 
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
however on reboot I have no signal to my monitor at all.

I'm sorry I can't offer more details but I don't know what details are important.

---

### Post by John.Michael.Kane on 2006-07-16
Heres some other guides if you try to reinstall [**[COLOR="Red"]UDSF-ATI[/COLOR]**]("http://doc.gwos.org/index.php/ATI") 

You can also try this before reinstalling```
**[COLOR="DarkOrange"]sudo dpkg-reconfigure xserver-xorg[/COLOR]**
```

---

### Post by ovimunt on 2006-07-16
I would strongly advise anyone to use the text mode installer as this can save you lots of hasle with the graphics. Anyway, when you install in text mode, at some point during the file installation it will try to detect your graphics hardware and will allow you to chose the resolutions you want to have available.

Besides, if you have graphics problems but still don't want to install in text mode you could try to select the safe graphics start option when the installation CD/DVD boots. This might actually give you a much more sensible resolution as it is supposed to use VESA which is a standard that works with ANY graphics card.

---

### Post by cosine7 on 2006-07-17
> **ljpm said:**
> Hi all,

I am a complete beginner so please keep all replies very simple.

I have installed 6.06 i386 on an AMD64 (heard i386 installed easier and was better than AMD64 bit version) with a Radeon ATI integrated video card and a sony (DVI) flat panel monitor. 

The screen resolution is set at 640 x 480. (this also make the installation difficult since all the windows are larger than the screen and have to be moved around)

I have tried to install the video driver according to 
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
however on reboot I have no signal to my monitor at all.

I'm sorry I can't offer more details but I don't know what details are important.



I had a similar problem turned out the driver did'nt like the DVI port, i have the radeon 9250 RV280, but still cannot get 3d working, but 2d is fine, but i have to use an anolog cable....

---

### Post by ljpm on 2006-07-18
Hi all,

Thanks for the responses. I will try again tonight. 

Here's an update on some recent attempts.

I used package manager to install driver-fglrx.
The installation seemed to go ok but I still couldn't change the resolution.

I then opened a terminal and entered
sudo aticonfig --initial
and then rebooted.

This resulted in no signal to my monitor via DVI.

I switched to the analog cable and received the following error from the monitor.
HD15 - out of range
Input 2: HD15
Resolution > 1280x1024

I will attempt to connect to an old CRT monitor tonight and see if I get a signle to the monitor.

Again, thanks for the help.

---

### Post by ljpm on 2006-07-19
Hi all,

Reconfiguring xserver-xorg (sudo dpkg-reconfigure xserver-xorg) sovled the problem, at least partially. I am now able to change the resolution of the screen, but only with the analogue cable to the monitor. This may be because I was using the analogue cable when I reconfigured xserve-xorg. I will try changing the to the DVI cable and reconfiguring again to see if I can get the monitor working with the DVI.

Thanks. (especially to SD-Plissken)

---

### Post by cosine7 on 2006-07-21
> **cosine7 said:**
> I had a similar problem turned out the driver did'nt like the DVI port, i have the radeon 9250 RV280, but still cannot get 3d working, but 2d is fine, but i have to use an anolog cable....

I hate to quote myself.... but i found that if i set the machine for automatic login, with the DVI cable to will boot fine into, gnome, but you will not see the login screen... (but still no 3d)

---

