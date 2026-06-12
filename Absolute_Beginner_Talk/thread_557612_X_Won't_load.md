---
title: "X Won't load"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Lee_Lee87 on 2007-09-22
Well this is my first post on these forums and probably not my last.I'm somewhat of a newbie to linux and trying to do my first install. I'm having trouble getting X to load when trying to install. I've opened up my xorg.conf using nano. I've notived that my onboard video is set as my primary device. I'm using a radeon 9250 (PCI) and was wondering what I can put in the device field to make my radeon the primary. Also is there a driver stored or on the cd that I could use. I'm assuming that "vesa" will work for the momoent, if there isn't one. And Lastly, I have my radeon installed in the 2nd pci slot. I ran lspci and it showed that it was in PCI:0:0a:0. Just need to know if I should put "PCI:0:0a:0" in the BusID field?

---

### Post by Linux_Man on 2007-09-22
Can your live-cd show up with X?

---

### Post by Lee_Lee87 on 2007-09-22
not quite sure what you mean?

---

### Post by Lee_Lee87 on 2007-09-22
sorry, had a brain fart:-k. No X doesn't load when I use the live-cd. I get the start or install screen, after
choosing that it loads linux kernal. Then goes into a Ubuntu loading screen. And alas comes the blue screen of death "failed to start X server..... It is likely it is not setup corrctly. View the X server output"
after viewing the output it shows another blue screen saying xserver is now disabled then shoots me to a command prompt "ubuntu@ubuntu"

---

### Post by st33med on 2007-09-22
Try using the Alternative CD.

---

### Post by asmoore82 on 2007-09-22
> **Lee_Lee87 said:**
> Well this is my first post on these forums and probably not my last.I'm somewhat of a newbie to linux and trying to do my first install. I'm having trouble getting X to load when trying to install. I've opened up my xorg.conf using nano. I've notived that my onboard video is set as my primary device. I'm using a radeon 9250 (PCI) and was wondering what I can put in the device field to make my radeon the primary. Also is there a driver stored or on the cd that I could use. I'm assuming that "vesa" will work for the momoent, if there isn't one. And Lastly, I have my radeon installed in the 2nd pci slot. I ran lspci and it showed that it was in PCI:0:0a:0. Just need to know if I should put "PCI:0:0a:0" in the BusID field?

you need to put ``PCI:0:10:0'' in the "BusID" field[[0x0a(*hexadecimal a*) is 10(*ten*) in decimal format]].
and either ``ati'' or ``radeon'' should work as the driver for your card.
``radeon'' has much better performance as it is specifically made for
Radeon cards but that shouldn't be of much concern for the install.
[[``fglrx'' is the name of the official ATI proprietary driver which you can
get post-install if you want]]

P.S. Linux doesn't have "Blue Screens of Death" ... a BSoD is when a certain
other "OS" crashes *completely*. the case of X not starting is far, far, far
less severe as the true multitasking Linux kernel is still working fine and
dandy and the GNU/Linux Operating System is still running in full
multi-user mode with networking :KS.

---

