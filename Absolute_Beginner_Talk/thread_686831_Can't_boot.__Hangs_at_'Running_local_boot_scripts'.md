---
title: "Can't boot.  Hangs at 'Running local boot scripts'."
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by hexagonsun on 2008-02-03
I managed to install ubuntu on my laptop and it seemed to boot fine right after install.  I have an external monitor that I use for my laptop so I selected ubuntu to use that as my default monitor.  After telling me to log out for the settings to take effect I was unable to log back in.  Now whenever I restart it hangs at this 'Running local boot scripts' and the screen flashes a few times before it finally just hangs.  I tried reconfiguring the Xserver-Xorg although this didn't seem to help as 'startx' claimed it could not find any monitors.  My laptop is an ASUSW3J with a ATI Mobility Radeon X1600, any suggestions?

---

### Post by Ub1476 on 2008-02-03
If you edit Xorg and use the vesa driver and use a low resolution, you're likely to be able to start X at least.

```
sudo nano /etc/X11/xorg.conf
```

To use the close and save key press <Control>+x (for close). It shows all options of course.

By the way, you know you have to press <Space> to select certain options when reconfiguring X?

---

### Post by PinkFloyd102489 on 2008-02-03
My server always hangs at boot scripts. I just hit Enter and the login prompt comes up for me.

Might want to check /etc/rc.local if you think something's up.

---

### Post by hexagonsun on 2008-02-03
Changing the driver to vesa allowed X to start although if I try to add the monitor again it goes back to same problem.  Should I look into installing one of these ATI drivers, would that help at all?

---

### Post by Rocket2DMn on 2008-02-03
I know you said you reconfigured X, but what about with -phigh
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
You can also try the proprietary drivers for ati:
```
sudo apt-get install linux-restricted-modules-generic restricted-manager
```
The "driver" in xorg.conf would "fglrx" instead of ati.

---

