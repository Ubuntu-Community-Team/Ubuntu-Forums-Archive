---
title: "How to kill X?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Iceni on 2007-04-05
Hey, I have a probably simple question. I need to kill X in order to install the official nvidia driver, but I can't for the love of my life figure out how to do it. I've even done it once before but can't remember how. 

Anyone knows?

---

### Post by taurus on 2007-04-05
```
sudo killall gdm
```

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Iceni on 2007-04-05
Thanks! I've used envy before, but it gave me an old driver. I'll give it another shot, I probably did something wrong:)

---

### Post by arbulus on 2007-04-05
I've been curious about that as well.  I've set my computer to boot to CLI first, and then I start the GUI when I need it.  Most people advocate just typing "startx" to do this, but I find that when I do, I can't kill it.  Usually I type:

sudo /etc/init.d/gdm start

(I use Gnome.  for KDE or XFCE you would use kdm or xdm)

Then when I want to stop it I type:

sudo /etc/init.d/gdm stop

And I'm right back to just the shell.  But if I just "startx" the gdm doesn't start, so you can't kill it this way.  But I've not been able to find the kill command for X, so I don't use "startx".

---

