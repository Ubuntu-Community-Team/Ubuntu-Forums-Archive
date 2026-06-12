---
title: "Ubuntu on a Dell Dimension 2350"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Ophidian on 2006-10-20
I plan on trying to install Ubuntu on an old desktop computer of mine--the only one I have avalible is a Dell Dimension 2350. I want to no longer have Windows XP on this desktop, I figure since I've been using Windows since 3.1 that it's about time I wean off of it.   
This computer is in okay condition; but the DVDROM and Floppy drive are no longer functioning, and 2 of the 4 USB ports are kind of tricky. (CDROM is working fine.) I haven't added anything to the hardware since I've bought this system new, which was some amount of years I've lost count on.

I'd buy a new DVDROM and maybe a stick of RAM for this computer... if I had money. I have no funds besides maybe two dollars in pennies.

I use a Linksys WRT54G router to let many computers in the home access Internet. Will Ubuntu have any conflicts with the router I use? The Dimension will be connected through Ethernet (not wireless).

I've done a little research on the Internet ahead of time, and found not much more than a lot of woe over installation on the Dimension 2350. 

Considering some limitations I have, what steps should I take before attempting to install Ubuntu? Is there a certain version which may work better with this hardware?

---

### Post by ReaderRat on 2006-10-20
Please tell us more about your hardware...RAM, video card, etc....

---

### Post by Kateikyoushi on 2006-10-20
I think because that system is older dapper and edgy supports your system equally well. How much ram does it have ? If 192 or more you can use the live cd to install.
Because you do not use wireless ubuntu should play well with your router.
In case you hit some landmines ask for help, there are plenty of helpful people on this board to aid you.

---

### Post by Old Pink on 2006-10-20
Try the Live CD. This will boot the OS from the CD itself. 

Although it's slow, and you can't modify anything without losing it at reboot, you'll get a brilliant idea of what works and what doesn't work. :)

---

### Post by underdog512 on 2006-10-20
I would consider using Xubuntu.  It is a light weight version of ubuntu and might work better givin your hardware limitations

---

### Post by Ophidian on 2006-10-20
> **ReaderRat said:**
> Please tell us more about your hardware...RAM, video card, etc....

There's only 128 of RAM. Pentium 4 processor (1.80GHz). Only one 55GB hard drive, any other details are hard to get. I think this computer uses an on-bard video controller (I don't know what they do off in dell-land...) I'm seeing a display adapter named Intel 82845G/GL/GE/PE/GV. 

Also, my netword adapter is Broadcom 440x 10/100.

---

### Post by matocha on 2008-06-15
Hello,
I have a Dell Dimension 2350 (256 MB RAM, 1.8 GHz Proc, 60 GB drive) as well with "INTEGRATED INTEL 3D AGP Video".  When I attempted to install Ubuntu 8.04 LTS Desktop from the CD I noticed I got a blank screen when I went to the "install" selection.  So instead, I installed with simple graphics mode.  This install worked however I'm saddled with 640x480 resolution.  If I look at the /etc/X11/xorg.conf it seems it has generic things in there.  How do I get it to recognize my integrated intel video so I can get a better resolution?

BTW, I have no graphics card, just the integrated video listed above.  My monitor is a GM-171B and the specs can be found here: [http://www.gemstarusa.com/index.php?option=displaypage&Itemid=134&op=page&SubMenu=](http://www.gemstarusa.com/index.php?option=displaypage&Itemid=134&op=page&SubMenu=)

What do I need to do to get this set up correctly?

---

### Post by matocha on 2008-06-17
Hello,
I figured it out by playing around with it.  The following goes in the /etc/X11/xorg.conf file:

Section "Device"
        Identifier   "Integrated Inted 3D AGP Video Controller"
        Driver       "i810"
        BusID        "PCI:0:2:0"
EndSection

I also had to fill in the appropriate Monitor and Screen sections given my hardware.  Thanks to the post here for information leading to me solving my problem:  [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

