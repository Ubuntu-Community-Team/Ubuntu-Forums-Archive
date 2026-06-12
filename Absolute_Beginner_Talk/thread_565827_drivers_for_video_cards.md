---
title: "drivers for video cards"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by chirawuf on 2007-10-02
I just installed ubuntu and I am new to linux.  my ubuntu installed perfectly except the driver for the video card.  My video card is Trident Video Accelerator Blade 3D/ProMedia from the Trident Microsystems manufacturer.  I have made attempts to visit the manufacturer website and I didnt get any drivers for linux.  I googled the drivers for the video card, I only find for windows.  

ubuntu installed a driver for the trident CyberBlade/il.  I can use the ubuntu right now, but the resolution on the monitor is not good.  

I need help finding the right driver or an alternative solution.  I also need help installing the driver.  Thank you for your help.

---

### Post by mysticmatrix on 2007-10-02
> **chirawuf said:**
> I just installed ubuntu and I am new to linux.  my ubuntu installed perfectly except the driver for the video card.  My video card is Trident Video Accelerator Blade 3D/ProMedia from the Trident Microsystems manufacturer.  I have made attempts to visit the manufacturer website and I didnt get any drivers for linux.  I googled the drivers for the video card, I only find for windows.  

ubuntu installed a driver for the trident CyberBlade/il.  I can use the ubuntu right now, but the resolution on the monitor is not good.  

I need help finding the right driver or an alternative solution.  I also need help installing the driver.  Thank you for your help.

Most of the time resolution problem is not due to drivers. Check this page for more information and possible solution to your problems. 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Also, as much as I know, you will have correct drivers installed by default.

---

### Post by master_kernel on 2007-10-02
I'm pretty sure the drivers are built into Ubuntu.

---

### Post by chirawuf on 2007-10-02
Thank you, I will try that.

---

### Post by BertP on 2007-10-03
I have the same **exact** problem.    I have Ubuntu installed on an old computer my brother discarded.

The motherboard seems to be a SOYO   SY-K7VEM Pro.   According to to the SOYO website, the embedded video is  "Embedded Trident Blade 3D AGP with 2M/4M/8M memory"

however my device manager in Ubuntu shows Cyberblade i1

With this configuration,  the highest resolution I can go to is 800/600.   If I switch 1024/768  I see sparkles; only a few at 60hz  more at higher frequencies,

chirawuf:  Did you find out anything else?
Anyone:  Is there a better driver available?

Thanks!

---

### Post by DeeJack on 2007-10-03
I don't know much myself. But iam here with a dual monitor situation. Actually Iam not using Ubuntu but Debian and is the computer iam using online now. But i did have to fix the Debian resolution. If you dont know -  a lot can be done editing the X11 files, a place to start, of course you can really mess up; so be careful. 
<a href="http://ubuntuforums.org/showthread.php?t=221174">The reason Iam here was due to this link</a> to this forum, you can use it to backup your /X11/xorg.conf file. The dpkg -reconfigure xserver-xorg was not found on the computer Iam trying to setup now which is (Rails Live CD). However; the dpkg cmd is a Debian command and Ubuntu is based on Debian (as I recall) and should work for you.

I hope this is better than nothing.

---

