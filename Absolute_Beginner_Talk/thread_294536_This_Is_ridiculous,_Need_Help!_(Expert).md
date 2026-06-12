---
title: "This Is ridiculous, Need Help! (Expert)"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by DanSchnell on 2006-11-06
I've been -attempting- to try the liveCD for Ubuntu 6.10 and 6.06 for the last month now and I can't get anything to work.

This is what happens when I try to boot ubuntu after the first option screen: 
[IMG]http://img.photobucket.com/albums/v512/tathar902/other%20stuff/screenshots/100_0151.jpg[/IMG]

Solutions I've tried:

Sudo dpkg-reconfigure xserver-xorg
-Setting driver to vesa
-setting monitor at medium setting
sudo /etc/init.d/gdm restart
-NOTE: Starting GNOME Display Manager...[FAIL] (WHY?!)
Sudo apt-get install nvidia-glx
Sudo nvidia-xconfig

Editing xorg manually doesn't work either...

Can somebody please help me!?

Graphics card= 2 of eVGA nVidia GeForce 6800GS CO running SLI
AMD 64 ASUS A8N-SLI Prem mottherboard

---

### Post by NPALeech on 2006-11-06
I have the same card (But not two of them...) Run it in safe graphics mode (option two.) That's what's always worked for me.

---

### Post by DanSchnell on 2006-11-06
Oh yeah, I've tried that too...still doesn't work.

Monitor= Samsung 19" (Optimum setting = 1280*1024 wth 60Hz refresh rate

---

### Post by user1397 on 2006-11-06
is SLI supported in ubuntu?  (does anyone know for sure?)

---

### Post by DanSchnell on 2006-11-06
I think it is, you have to enable it in xorg.conf though, which I haven't done.  But I should still be able to load ubuntu even if it isn't enabled or only using one...

---

### Post by DanSchnell on 2006-11-06
Somebody please!

---

### Post by John.Michael.Kane on 2006-11-06
Why not try booting with a single monitor connected to your machine. get it configure,and then move to configuring the second one.

---

### Post by dpar on 2006-11-06
I had that happen until I got my video drivers configured right. My monitor will do both digital and analog, if you switch from analog to digital, everything should look ok.
On mine I can push a source button on the monitor.

---

### Post by tronica on 2006-11-06
don't use SLI until you get the nvidia driver installed, so take out the other card, run in single. Install the drivers, then put in the other card.

To enable SLi, after installing the nvidia drivers

> nvidia-xconfig --sli=on

---

### Post by DanSchnell on 2006-11-07
Are you sure thats what is causing the problem?

---

