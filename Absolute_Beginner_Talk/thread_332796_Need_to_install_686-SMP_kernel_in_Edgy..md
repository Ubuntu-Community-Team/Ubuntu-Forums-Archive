---
title: "Need to install 686-SMP kernel in Edgy."
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by RussianVodka on 2007-01-06
To fix some of the problems associated with installing Edgy (like no out of box WiFi support) I decided to first install Dapper, and then upgrade to edgy.

Using a guide recently posted on Digg, I updated successfully. Except for one problem. Unlike Edgy, in Dapper came with only a i386 kernel and you had to install the others on your own. So, now, since I didn't install the new kernel in Dapper, I'm stuck with a i386 kernel in Edgy.

*uname -r* gives me *2.6.17-10-386*

So, no problem I thought  to myself. I booted up Synaptic, and searched for "SMP". The problem is that all the kernel files have an "Obsoleted" message next to them. So I said screw it, and installed it anyways. Not my GRUB screen has (had, I uninstalled back to original settings) amongst the previously installed kernels, a "###-generic" kernel (where ### represents some numbers).

When I boot up like that, I do get my 686-SMP support, but some of my devices (namely the WiFi card) don't work.

How would I go about solving this?

---

### Post by Ocxic on 2007-01-06
the generiv kernel is used to replace all the differnet ones from previous versions.

to get your wifi card working try re-installing the drivers. id your card worked right after your first install try removing and re-installing the linux-restricted-modules pakage in synaptic. and reboot

---

### Post by RussianVodka on 2007-01-06
> **Ocxic said:**
> the generiv kernel is used to replace all the differnet ones from previous versions.

Should I install the "linux-image-generic" or "linux-generic" metapackage?
> 
to get your wifi card working try re-installing the drivers.

Damn it! But that's the reason I'm doing all this instead of just installing Edgy. I dont' want to bother with the driver.

Oh well.

---

