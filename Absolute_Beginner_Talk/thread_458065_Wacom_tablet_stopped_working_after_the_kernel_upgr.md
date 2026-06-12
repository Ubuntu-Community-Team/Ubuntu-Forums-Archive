---
title: "Wacom tablet stopped working after the kernel upgrade"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by onero on 2007-05-29
Sorry, another kernel upgrade issue. I upgraded to the 2.6.20.16 low latency kernel in Feisty, and now my Wacom Intuos 3 6x8 tablet is not responding. I already installed the linux-headers for both the generic and low latency kernels, and tried reinstalling the wacom packages (wacom-kernel-source, wacom-tools, xserver-xorg-input-wacom) several times, but this didn't work either. Before the upgrade, my wacom tablet was working (buggy, but working, and usually I could get it to respond by restarting X). 

Also, this might be of use: when reinstalling wacom-kernel-source, it give the following error:

Error: kernel headers not found in '/usr/src/linux'


But, as I mentioned previously, linux-headers is already installed for both generic and lowlatency kernels (and for both kernels 2.6.20-15 and 2.6.20-16, too). Any ideas as to how I can solve this? Thanks!

---

### Post by onero on 2007-05-29
Update: I fixed the kernel headers not being found by linking the usr/src/linux folder to linux-headers-2.6.20-16-lowlatency (sudo ln -s linux-headers-2.6.20-16-lowlatency/ linux), but it's spitting out a new error now when I try to reinstall wacom-kernel-source:

E: wacom-kernel-source: subprocess post-installation script returned error exit status 2


Prior to that, I got a warning that the kernel headers don't match the running linux version, but uname -r returns 2.6.20-16-lowlatency. Can anybody help out? Thanks!

---

### Post by thedaemon on 2007-07-11
Check your xorg.conf file and see if it changed.

---

