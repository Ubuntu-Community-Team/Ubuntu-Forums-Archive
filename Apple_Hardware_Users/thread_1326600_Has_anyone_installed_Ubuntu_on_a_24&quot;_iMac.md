---
title: "Has anyone installed Ubuntu on a 24&quot; iMac?"
date: 2009-11-14
forum: Apple Hardware Users
---

### Post by zanyjazz on 2009-11-14
If so you can possibly help me.

---

### Post by realzippy on 2009-11-14
Seen this?

[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

---

### Post by zanyjazz on 2009-11-14
He says 'make sure that 3D acceleration is working', well it isn't but there is no indication of how to get it to work. Every avenue I have gone down so far has resulted in a similar dead stop.

---

### Post by realzippy on 2009-11-14
And he says:

Intel Graphics

For iMac users with Intel graphics (some early white Intel iMacs), everything should be working out-of-the-box. If you have have any problems, be sure that your xorg.conf is set to use the 'intel' driver rather than the any of the other specialized Intel drivers like 'i810'.
ATI Graphics

For ATI graphics, you will need to install the proprietary graphics drivers. This can be done with the Driver Manger in System > Adminstration > Driver Manager. When installed correctly, reboot, and an additional check is to run
fglrxinfo
The output should tell you that the provider is ATI and not MESA.


If you have issues with the driver in the Ubuntu repos, you can alternately try Envy or even download the driver from ATI's website and install manually.

[I]It depends on the graphic card.
But under Karmic/Jaunty ATI maybe a problem depending on the card.[/I]

---

### Post by zanyjazz on 2009-11-14
Downloaded graphics driver for ATI, would not install, not compatible.
Downloaded Envy and ran it. Only ATI driver not compatible. Installed it anyway, totally screwed the system.
A number of users have advised editing xorg.conf but there is no such file!
I think it is reasonable to assume that my iMac and Ubuntu 9.10 are not compatible!!
I have removed Ubuntu from my system. I wonder if an earlier release may work better?

---

### Post by realzippy on 2009-11-14
If it has ATI graphics,8.10 is fine.

---

### Post by zanyjazz on 2009-11-15
It has ATI graphics. I have switched from 9.10 to 8.04 but still have the same problem. I must be missing something somewhere!

---

### Post by howefield on 2009-11-15
Is this the same issue described in your other post involving Virtualbox ?

---

### Post by zanyjazz on 2009-11-15
The screen resolution problem appears solved but everything has slowed down. Can't have everything I suppose.

---

### Post by randallsquared on 2009-11-15
I'm using Ubuntu on an imac7,1 (a 24" iMac from late 2007) right now.  The Ubuntu 9.10 proprietary ATI drivers destroyed my first attempt (hard lockup; couldn't even get another virtual console up or kill X, and then when I restarted the filesystem was trashed, too).  However, downloading the latest ATI drivers from ati.amd.com worked like a charm.  I also avoided installing the proprietary Broadcom drivers, since I don't use wifi, so I can't say whether those work well.

---

### Post by Nohtanhoj on 2009-11-16
What version of the drivers did you use? So far, all I can see are drivers for Win7 and XP.

---

### Post by randallsquared on 2009-11-20
At ati.amd.com , I selected the Graphics drivers, and then in the second dropdown the Linux OS.  Not sure why you'd only see Windows in that dropdown.

---

### Post by Nohtanhoj on 2009-11-20
Simple solutions... I'm getting my Ubuntu on as we speak. Thank you!

---

