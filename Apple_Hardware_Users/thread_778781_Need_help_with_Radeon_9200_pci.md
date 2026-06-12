---
title: "Need help with Radeon 9200 pci"
date: 2008-05-02
forum: Apple Hardware Users
---

### Post by smileyme on 2008-05-02
I recently acquired a Radeon 9200 for my 500 Mhz G4 upgraded B&W. Works great in OS X, but I can't seem to get it working in Ubuntu. When I boot, the display is scrambled. After reconfiguring xserver-xorg, and telling it to reboot, I see the Ubuntu shut-down spash, but when it reboots, it's scrambled again. 

Rick :)

---

### Post by stream303 on 2008-05-03
Which version of PPC Ubuntu are you running?  Also, what is the make/manufacturer of your monitor, particularly it's native resolution?

Have you tried using the *nosplash* and/or *video=ofonly* kernel parameters at the second-stage boot prompt?  (just hit -tab- to stop the automatic countdown) and type in the parameters you want to try.

Hopefully that will get you some boot messages scrolling past.  No Ubuntu splash screen has every looked that good for me btw, so I always like to see boot messages instead.

As for reconfiguring xorg.conf - in Hardy the old dpkg-reconfigure xserver-xorg does not really work well and is being deprecated - but if you are running an older distro it is ok.  However, your box will need some tlc.  Check these out for info on the ATI cards:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

For my money, I'd disable all the fancy stuff first, like glx, dri, etc and focus on just getting the right resolution going first - then adding things back in.

A few more knowledgable ATI owners are on board, and have some good threads about bad screens..

---

