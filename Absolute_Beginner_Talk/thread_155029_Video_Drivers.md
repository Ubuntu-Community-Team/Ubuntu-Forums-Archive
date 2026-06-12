---
title: "Video Drivers"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by ZiGz on 2006-04-04
I have installed 5.04 on a IBM 8313-LCU machine and I only have option for 640x480 what should I do?  Will upgrading to Breezy have any chance of fixing this?

---

### Post by meborc on 2006-04-04
you can reconfigure your xserver:
**dpkg-reconfigure -phigh xserver-xorg**

or you can manually edit your xorg.conf file to get bigger rezolutions...

[B]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo gedit /etc/X11/xorg.conf[/B]

now add find the place where "640x480" is typed... there should be several places/lines... now add "1024x860" (or whatever your resolution should be) in front of the "640x480" ... so it should look like ```
"1024x860" "640x480"
```
in those places... don't erase anything!

also try installing your 3dcard driver (if you haven't done it already)... for that search the [wiki]("https://wiki.ubuntu.com")

if you mess up then just:

**sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf**

there are a lot of threads about resolution here in beginners section... use search to get them...

---

### Post by ZiGz on 2006-04-04
thank goodness for Dual-Boot
I had tried to reconfigure x-server but now I have no Gui.  Will prob just reinstall Ubuntu  and try your second suggestion.

thanks

---

