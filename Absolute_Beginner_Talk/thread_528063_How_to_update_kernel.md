---
title: "How to update kernel?"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by pointyblue on 2007-08-17
I'm running Xubuntu 7.04 with kernel 2.6.20-15.27-generic. I need to update the kernel as it can't find and configure my PS/2 mouse.

Which command do I enter in Terminal, and will everything work afterwards or do I need to make additional upgrades?

---

### Post by diatribe on 2007-08-17
you could try sudo apt-get dist-upgrade

dont know if it will accomplish what you want though

---

### Post by Inxsible on 2007-08-17
you can search for the specific kernel number in Synaptic and install it from there.

---

### Post by igknighted on 2007-08-17
Try this guide, worked perfectly for me.  You will have to install programs like Madwifi, nvidia/ati drivers, etc. manually though because the kernel modules in the repo don't work with custom compiled kernels.

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by az on 2007-08-17
> **pointyblue said:**
> I'm running Xubuntu 7.04 with kernel 2.6.20-15.27-generic. I need to update the kernel as it can't find and configure my PS/2 mouse.

Which command do I enter in Terminal, and will everything work afterwards or do I need to make additional upgrades?

You probably need to reconfigure the X server instead.  To be sure, boot into recovery mode and run

dpkg-reconfigure -plow xserver-xorg

and when it asks about mouse device configuration, try picking the other option (if you have any, ex /dev/psaux)

keep answering the questions to the end - take the default for everything.

Run 
init 2
to get back into graphical mode.  If that worked, please file a bug report  - you should not have to reconfigure your mouse like that.  Actually, either way, please file a bug report.

---

### Post by pointyblue on 2007-08-19
I tried

```
sudo apt-get install linux-image-generic
```

which updated the kernel and everything is working ok now.

Thanks for trying to help out!

---

