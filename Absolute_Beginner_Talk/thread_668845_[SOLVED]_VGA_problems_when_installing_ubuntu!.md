---
title: "[SOLVED] VGA problems when installing ubuntu!"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Mats_swe on 2008-01-15
Hi everyone, I would need some help with installing ubuntu linux 7.04 on my laptop. I already have Vista installed.

When I start the installation with the live CD it after a while says: "Xserver disabled. Restart GDM when configured correctly."

I then type sudo dpkg-reconfigure xserver-xorg and make the settings. Then I come to the command line. A tried to type
startx
but then it complains that it can't use 24-bit color mode with the screen. (I also tried choosing 16-bit). Anyway, it complains about the driver. I have a standard VGA graphical card and uses 32-bit colors in Vista.

Then it shuts down the installation and windows starts.

What should I do to fix this? Do I need to install some driver or is there another way to get around it?

Please help me. I'm quite new to this and would really want to install linux.
I have a AMD64 Athlon X2 processor and used a live-cd with ubuntu-desktop-7.04-amd64.
//Mats

---

### Post by steveneddy on 2008-01-15
Try the **vesa** driver.

---

### Post by Mats_swe on 2008-01-16
It didn't work with the VESA. It says the same thing.

---

### Post by Mats_swe on 2008-01-16
More exactly it says
(EE) VGA No matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error
     No screens found

---

### Post by Mats_swe on 2008-01-18
It finally worked:

[http://ubuntuforums.org/showthread.php?p=4161343#post4161343](http://ubuntuforums.org/showthread.php?p=4161343#post4161343)

---

