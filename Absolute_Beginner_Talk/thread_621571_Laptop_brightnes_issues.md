---
title: "Laptop brightnes issues"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Onay on 2007-11-23
For some reason, although I have altered the power management and made sure that the screen is full brightness and doesn't dim, the screen still automatically dims and is always at least brightness during startup.

I can change the brightness using the laptop keyboard shortcuts, but it always seems to reset whenever I do certain things or let the laptop idle for 1 minute. How can I change this?

By the way I own a Thinkpad Lenovo T60 and I'm running Gutsy.

---

### Post by dips_xe on 2007-11-23
i'm also on a thinkpad t60 on gutsy and have problems with the brightness. fn+home/end don't do anything, so its always full brightness. i was told to "blacklist video", maybe that will fix your problem as well, but i forgot in what configuration file to put blacklists in. 

by the way, do you have an ati or intel card?
unrelated to your problem, i'm having one

---

### Post by Onay on 2007-11-23
Ati X1400 128 mb graphics card.

/etc/modprobe.d is where the blacklists are placed, but which one do I comment out?

---

### Post by dips_xe on 2007-11-23
don't comment out anything, just add "blacklist video" to /etc/modprobe.d/blacklist . i'm going to try it right now and see if it makes my brightness behave...

edit: this worked to fix my brightness problem, so its at least worth trying for you

---

### Post by Onay on 2007-11-23
Well I'm not using the vesa driver, I'm using an ATI driver. Blacklisting video would really screw up my system.

---

### Post by MozartlovesUbun2 on 2007-11-23
[B]yes screen dims down while watching a movie, how dumb is that!!!

[/B]

---

### Post by to young on 2007-11-24
Yes I am having similar problem.  Although I am not using a laptop.  

The brightness dims down after a while or when the screensaver comes on.  

I have to relaunch Nvidia settings.  however as soon a nvidia settings are launched the brightness increases to adjusted values.  My solution to this was to keep the nvidia settings window open all the time.  

However, since I upgraded to gutsy it is not even doing that.  I have to close and re open nvidia settings to increase the brightness to desired level.  

very annoying please help.

---

### Post by runemaste644 on 2007-11-24
Have you tried Fn+F10 and Fn+F11? I have a different laptop, but its from the same manufacurer, so keybindings might be the same.

---

### Post by dips_xe on 2007-11-24
> **Onay said:**
> Well I'm not using the vesa driver, I'm using an ATI driver. Blacklisting video would really screw up my system.

i'm not using a vesa driver, i'm on an intel driver.

---

### Post by sdyson on 2007-12-08
You might have the problem discussed in this thread: 

[http://ubuntuforums.org/showthread.php?t=581335&highlight=thinkpad+screen+brightness](http://ubuntuforums.org/showthread.php?t=581335&highlight=thinkpad+screen+brightness)

The power settings dialog is confusing. The battery settings define how much to dim the display by, not how bright it should be, so 100% results in the darkest setting.

---

