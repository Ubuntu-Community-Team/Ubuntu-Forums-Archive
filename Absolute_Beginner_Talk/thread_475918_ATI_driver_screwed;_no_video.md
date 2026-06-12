---
title: "ATI driver screwed; no video"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by caughran on 2007-06-16
I downloaded an ATI driver installer from [http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)
and it seemed to go well. the program aticonfig crashed, however, leaving the parameters file in what seemed to be OK, if not optimized shape.

Booting this afternoon, however, I get past the Ubuntu splash-thermometer, and it displays only a box that shouts ANALOG OUT OF RANGE 83.7 kHz / 60 Hz.

I don't know where to go from here. How can I recover?

---

### Post by finer recliner on 2007-06-16
restart you computer in recovery mode (makes you root in a shell with no gui)

type this command to reconfigure your xorg.conf file
```

dpkg-reconfigure xserver-xorg 

```

most of your settings should be automatically found, so just press enter at most of the screens.

restart into normal mode.

check out this page to install ATI drivers instead of downloading directly from ATI website:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Dfnoboy on 2007-06-16
I had the same problem, and I used the command you provided, but when I boot in normal mode it says it can't find a screen...


Is there a way to start Ubuntu in a safe graphics mode from the boot? Right now I am running from the Live CD, and have Ubuntu installed onto the HD.

---

### Post by skymera on 2007-06-16
did u get the driver from Restricted Drivers Manager?

---

### Post by Dfnoboy on 2007-06-16
Yes.

I would like to disable it again >.>

---

### Post by skymera on 2007-06-16
go back and untick the box?

---

### Post by Crafty Kisses on 2007-06-16
> **caughran said:**
> I downloaded an ATI driver installer from [http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)
and it seemed to go well. the program aticonfig crashed, however, leaving the parameters file in what seemed to be OK, if not optimized shape.

Booting this afternoon, however, I get past the Ubuntu splash-thermometer, and it displays only a box that shouts ANALOG OUT OF RANGE 83.7 kHz / 60 Hz.

I don't know where to go from here. How can I recover?

After you reconfigure your X server file you should back your X server up, you can do this by doing the following:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then if anything ever goes wrong you can quickly recover it by doing the following:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

---

### Post by caughran on 2007-06-16
thanks, 
dpkg-reconfigure xserver-xorg
seemed to do it, after a misread of my notes had me trying a -reconfigure ooption on dpkg (there isn't one).

Seems to because the first boot left a blank screen. But I'm here now, and hopeful.

Thanks, again.

---

