---
title: "[SOLVED] How can I recover Gutsy Desktop"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-10-28
I have two monitors connected to ATI x1900 series graphics card.  I was under the screen and graphics tab and I could not tell which monitor was primary and which was secondary and I changed the refresh rate of the monitor that I thought was primary and now when I boot I hear the drum and cant see anything.   I enter the user name and password even though I could not see the place to enter them but my desktop never shows up.  I would like to get some assistance to fix this problem.

Thx in advance,

VC

---

### Post by carlosjuero on 2007-10-28
One option would be to boot into safe mode and, if you installed the official ATI drivers, type in
```
aticonfig --initial --force
```
which will reset your ATI driver installation/configration to default.

---

### Post by Colro on 2007-10-28
After hearing the drum, check if you're able to enter the terminal with control+alt+F1. If so, try running :
dpkg-reconfigure xserver-xorg

Just choose the defaults unless you know for a fact that something should be different. That should reset your video settings after it's done.

---

### Post by videocheez on 2007-10-28
Thanks guys here goes nothing.

---

### Post by Colro on 2007-10-28
Either one of those should work, good luck :)

---

### Post by videocheez on 2007-10-28
Ok guys.  I tried the "dpkg-reconfigure xserver-xorg" approach and I was able to recover my desktop so thanks a lot for your help.  My immediate problem is temporarily solved.  Can I edit the xorg.conf file with a text editor or do I have to use that funny DOS like program to make changes.  I need to configure both of my monitors and i noticed that all of the resolution info for my secondary monitor is not listed in the screens&graphics tab.  
Also I want to ask that would you say that my default monitor is the one that the login info appears on when i first turn on my computer?

Thanks ina dvance ,

VC

---

### Post by Colro on 2007-10-28
You can edit your xorg.conf with a text editor, but be careful what you change as it's quite easy to break things when you manually edit it. I'd reccomend using a guide or a GUI application to make whatever change you're wanting to make. Reguardless,
```
sudo gedit /etc/X11/xorg.conf
```
will let you edit it.

I can't help beyond that, though, I've never used a 2 monitor setup.

---

### Post by videocheez on 2007-10-28
Roger that.  You helped me to get my GUI back and that's huge:)

---

