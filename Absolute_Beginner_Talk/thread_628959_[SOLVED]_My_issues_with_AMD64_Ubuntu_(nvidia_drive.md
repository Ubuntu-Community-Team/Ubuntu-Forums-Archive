---
title: "[SOLVED] My issues with AMD64 Ubuntu (nvidia drivers, flash player)"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by debs083 on 2007-12-01
Hi there! I'm totally new to Linux so I've been struggling alot trying to install my nvidia 7100 drivers. I was recently on Mandriva 2008 but I had alot of trouble there too with my drivers, so I was told that Ubuntu 7.10 was better and easier, so I switched to it.
I was also told to download the x86 architecture version, I did, and burned the image on a CD, but after booting it and pressing the install option it said something about error reading CD. So I downloaded the 64 AMD version, and it installed fine. (My processor is an AMD64 Athlon)
However I'm having some trouble with this version, I try to install Adobe Flash Player and it says it's incompatible with the amd64 version. Also I can't install the nvidia drivers and almost every application from the Add/Remove Applications because it says it can't be installed on an amd64 system.
Is there any way to get around this issue? Or for installing the x64 version?

Another thing, I downloaded the linux nvidia drivers from the official nvidia site, but when installing it says that I need something called libc, any help on how can I get that?

Help will be greatly appreciated, thanks in advance! :)

---

### Post by overdrank on 2007-12-01
> **debs083 said:**
> Hi there! I'm totally new to Linux so I've been struggling alot trying to install my nvidia 7100 drivers. I was recently on Mandriva 2008 but I had alot of trouble there too with my drivers, so I was told that Ubuntu 7.10 was better and easier, so I switched to it.
I was also told to download the x86 architecture version, I did, and burned the image on a CD, but after booting it and pressing the install option it said something about error reading CD. So I downloaded the 64 AMD version, and it installed fine. (My processor is an AMD64 Athlon)
However I'm having some trouble with this version, I try to install Adobe Flash Player and it says it's incompatible with the amd64 version. Also I can't install the nvidia drivers and almost every application from the Add/Remove Applications because it says it can't be installed on an amd64 system.
Is there any way to get around this issue? Or for installing the x64 version?

Another thing, I downloaded the linux nvidia drivers from the official nvidia site, but when installing it says that I need something called libc, any help on how can I get that?

Help will be greatly appreciated, thanks in advance! :)

Hi maybe this link will help with the flash
[http://packages.ubuntu.com/gutsy/web/flashplugin-nonfree](http://packages.ubuntu.com/gutsy/web/flashplugin-nonfree)
and Have you tried Envy for the nvidia drivers
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Or you could try the restricted drivers located under system, administration, restricted drivers.

---

### Post by debs083 on 2007-12-01
Hi overdrank

Thanks for the flash tutorial, I will take a look.
As for the drivers, I tried activating them on the restricted drivers, but I get a message saying this: The software source for the package nvidia glx-new is not enabled.
In Envy, when I try to install it, I get this message: Error; Dependency is not satisfiable: xserver-xorg-dev . And I can't install it... How can I fix this?

Thanks in advance :)

---

### Post by rsambuca on 2007-12-01
Your repositories are messed up.  Go to System-Administration-Software Sources.  Make sure all of the boxes are checked.  Then press the "Download from" button and select "Other".  Press the "Select Best Server" button.  The program will test the servers and pick the quickest current one to you.  Then press the "Choose Server" button.

Update the repositories when prompted.  You can then install java by just going to a site that requires it (such as youtube).  You will be prompted to install Flash, select the Adobe flash plugin and you are done!

---

### Post by debs083 on 2007-12-02
W00t, everything seems to be working like a charm now!
Thanks alot for your help rsambuca and overdrank! :D

---

