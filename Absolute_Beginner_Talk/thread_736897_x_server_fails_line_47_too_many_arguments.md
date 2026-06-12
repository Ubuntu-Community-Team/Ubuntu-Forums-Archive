---
title: "x server fails line 47 too many arguments"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by BachNation on 2008-03-27
I just got an ati x1600 and when i install the drivers for 3d acceleration, and then restart the x server fails with error "too many arguments on line 47"and im stuck in terminal. Ive been having a lot of trouble with this. Any help is appreciated

---

### Post by Ub1476 on 2008-03-27
```
sudo nano /etc/X11/xorg.conf
```

Check out line 47 and post it here. If you installed it into an existing Ubuntu installation, I suppose you remember to remove the old driver first?

---

### Post by BachNation on 2008-03-27
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "&#65533;"
        Option          "DPMS"
EndSection


the problem is when i have to restart from installing the driver the gui fails to load because of the xserver xorg line argument. is there a way to get the gui back after this happens? because i have been having to reinstall everytime it doesnt work.

---

### Post by Ub1476 on 2008-03-27
If you only have one driver installed, you can try to reconfigure X:

```
sudo dpkg-reconfigure xserver-xorg
```

Press <Space> to select options. At the driver section, "fglrx" should be correct if you use Hardy Heron with drivers downloaded form Envy or Hardware Drivers.

---

### Post by BachNation on 2008-03-27
yea ive tried to reconfigure but it did not work. the driver i download is from the restricted driver one that it picks automaticaly. are you saying i should get a different one?

---

### Post by BachNation on 2008-03-27
when i go to device manager it shows the card twice but one says secondary after. does this mean i have two drivers installed?

---

### Post by Ub1476 on 2008-03-27
No, the drivers from RDM usually is fine, but they do not work for every card (especially new). If you only downloaded from there, there's only one driver you are using. Do you still get the line 47 error if you reconfigure X? Have you tried to remove it, reconfigure and use Envy to fetch the latest driver instead?

---

### Post by BachNation on 2008-03-27
yes when i used the RDM driver and reconfigure x it still doesnt work. so i should take the card out put it back in, then install the driver then configure x? and how do i use envy? is it a website?

---

### Post by BachNation on 2008-03-28
[solved] downloading updates and using envy to install drivers seemed to work.

---

