---
title: "[SOLVED] New monitor, bad resolution"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2007-12-25
I just got a Samsung SyncMaster 932BW and I can't get full resolutions from it. I know my graphics card can go higher than 1280x768 1280x800 1280x960 1280x1024. How can i go about getting the right resolution to work? I have the driver cd that I got with the monitor, but sadly it is a windows driver cd. Can I use that somehow? Any help would be appreciated, thanks.

---

### Post by taurus on 2007-12-25
You just need to reconfigure your X server with the new monitor.

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, restart X again with <Ctrl><Alt>Backspace.

---

### Post by califman831 on 2007-12-25
you can also restart x by typing startx at the command prompt

---

### Post by taurus on 2007-12-25
> **califman831 said:**
> you can also restart x by typing startx at the command prompt

Not if you already have gdm running.

---

### Post by slughappy1 on 2007-12-25
what do I need to reconfigure? As in what do I need to change? I haven't had much luck with doing sudo dpkg-reconfigure before. Although I haven't used -phigh xserver-xorg before. What does it do?

---

### Post by taurus on 2007-12-25
It changes screen resolutions for you, keeping everything else the same.  What graphic card do you have on that machine anyway?

---

### Post by slughappy1 on 2007-12-25
I'm not sure what exact card I have. I can't see any model numbers on the card. I know that I have an nvidia card, that uses the "NVIDIA accelerated graphics driver (latest cards)" driver.

Actually I went into the Device Manager and it says that I have GeForce 6200

---

### Post by slughappy1 on 2007-12-25
That code will change the /etc/X11/xorg.conf file, right?

---

### Post by taurus on 2007-12-25
It will save the current one to /etc/X11/xorg.conf.20071225 in case you need to use it again later.

---

### Post by slughappy1 on 2007-12-25
problem, I enter the command and it does nothing

jason@jason-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071225182512
jason@jason-desktop:~$ 

What's wrong?

---

### Post by slughappy1 on 2007-12-26
anyone?

---

### Post by slughappy1 on 2007-12-26
not quite sure why, but when I rebooted (twice I think) it now has a lot more resolution sizes. And more important the one best suited for my monitor. Thanks for you help anyway

---

### Post by GSF1200S on 2007-12-26
> **slughappy1 said:**
> not quite sure why, but when I rebooted (twice I think) it now has a lot more resolution sizes. And more important the one best suited for my monitor. Thanks for you help anyway

FYI- When you entered the command, you regenerated a new xorg.conf. All the terminal was telling you was that xorg.conf was re-written, and the old xorg.conf was saved as a backup. What driver did you select? Im just seeing if you have 3d accel from your video card. If you use the restricted drivers manager, it probably has configured the drivers for you...

---

### Post by slughappy1 on 2007-12-26
I'm not quite sure what you mean by what driver I chose. Are you talking about when the restricted drivers came up or when I entered the command that was given? Because for the restricted driver, only one was available. And for the command, that is what came up. Nothing else came on the screen, I typed in the command and it spit out what I posted above. Are either what you wanted to know?

---

