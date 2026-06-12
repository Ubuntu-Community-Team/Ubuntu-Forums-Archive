---
title: "Failed to start X server. Problem please help !"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-24
I downloaded and installed the ATI drivers from the ATI site.
Anyway the point is that I can no longer login with a graphical interface.

could you please tell me the commands that could help?

Maybe uninstall every graphics driver on there and then get the default once from the repository.
Any other way to make it work?

Thanks in advance

---

### Post by overdrank on 2007-06-24
> **ROUBOS said:**
> I downloaded and installed the ATI drivers from the ATI site.
Anyway the point is that I can no longer login with a graphical interface.

could you please tell me the commands that could help?

Maybe uninstall every graphics driver on there and then get the default once from the repository.
Any other way to make it work?

Thanks in advance

Hi if you will use the  ctrl,alt,F1 keys after the grub loads it will take you to the terminal then you can login and 
 enter sudo dpkg-reconfigure -phigh xserver-xorg. hope this helps;)

---

### Post by ROUBOS on 2007-06-24
thanks for that.
the command worked and I'm now within X again

So how do I uninstall all installed video drivers and install the correct ones?

I tried everything but I can't get Beryl work with th ATI Restricted driver enabled.

---

### Post by overdrank on 2007-06-24
> **ROUBOS said:**
> thanks for that.
the command worked and I'm now within X again

So how do I uninstall all installed video drivers and install the correct ones?

I tried everything but I can't get Beryl work with th ATI Restricted driver enabled.

Hi are you using a "how to" to install beryl, if you would do a quick search of your video card you might find some help or a "how to" to get you going.;)

---

### Post by Crafty Kisses on 2007-06-24
> **ROUBOS said:**
> thanks for that.
the command worked and I'm now within X again

So how do I uninstall all installed video drivers and install the correct ones?

I tried everything but I can't get Beryl work with th ATI Restricted driver enabled.

You should back up your X server, just in case anything ever happens again. ;)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

