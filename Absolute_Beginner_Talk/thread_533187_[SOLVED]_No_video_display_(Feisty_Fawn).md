---
title: "[SOLVED] No video display (Feisty Fawn)"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by corncob on 2007-08-23
I installed the restricted driver for my Nvidia card in preparation for installing TwinView for my dual monitor setup.  I rebooted the computer as instructed but now, after the initial startup, I just get a blank screen. (I rebooted several times).  Ubuntu is probably running but I can't see anything so I can't uninstall the restricted driver.  I can boot into recovery mode but don't know what to type at the command prompt.  Incidently, I had it working fine before but I reinstalled it because I thought I had messed it up  -- now it really is messed up.  I used a different disk for the 2nd install.  Ray

---

### Post by w4ett on 2007-08-23
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "nv" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:
```
startx
```

This will get you to a GUI desktop.  the go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.

---

### Post by corncob on 2007-08-24
Thank you, w4ett.  It worked and I'm back in business.

---

### Post by ddrichardson on 2007-08-24
If you mark this thread as solved it can help others with the same problem.

---

