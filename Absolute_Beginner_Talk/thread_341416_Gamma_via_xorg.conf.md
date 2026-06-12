---
title: "Gamma via xorg.conf?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by online14230 on 2007-01-18
Hi there.
Quick question: Is there any way to use the /etc/X11/xorg.conf to set gamma correction? I just figured out that you can use xgamma, but then it isnt persistent. Id like to make the correction and NOT worry about it again. I can also create a launcher and put it in tstartup, but Id like to know if there are any other ways...
please help!!

Oh yeah, ATI Radeon 9200SE

---

### Post by z0r on 2008-04-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/33214](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/33214) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Just in case you're still looking, yes it can be done. Search for "gamma" in the manual: [http://www.x.org/archive/X11R6.9.0/doc/html/xorg.conf.5.html](http://www.x.org/archive/X11R6.9.0/doc/html/xorg.conf.5.html)

My /etc/X11/xorg.conf monitor section now looks like this (Ubuntu 8.04):
```
Section "Monitor"
        Identifier      "Configured Monitor"
        Gamma           1.03 0.86 0.67
EndSection
```
These settings are also restored after using gnome-screensaver (unlike using xgamma).

---

