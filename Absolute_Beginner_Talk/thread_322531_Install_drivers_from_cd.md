---
title: "Install drivers from cd"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by bjauk on 2006-12-20
I just bought a new laptop: HEL80
- INTEL CORE 2 DUO T7200 2GHZ S478
- 1024MB 667MHZ DDR2 SODIMM RAM 
- 100GB SATA 7200RPM 2.5"
- Nvidia GeForce Go 7600 w/ 256MB ded. memory

and with it came a cd with drivers. Now, when I try to install a driver, I get this nice message:

Cannot open /media/cdrom0/driver/Bluetooth/Setup.exe: No application suitable for automatic installation is available for handling this kind of file.

Okay, that seemed like there might be an easy way out of this, but bearing I'm a complete newbie when it comes to Linux and Ubuntu, I might need some help. A lot actually.....

---

### Post by Swab on 2006-12-20
That looks like a Windows program for installing Windows drivers.   It will never work in Linux.  

Is the machine working well in Ubuntu?

---

### Post by bjauk on 2006-12-20
It's not easy to say if it works fine, since I don't have anything running on it. Had some problems with 1st boot after install, where it seemed to freeze up. I shut it off and the same thing happened. The third time, I applied the live-cd (from where I installed) and then it started perfectly (meaning started the installed version and not the live one). The company that buildt the lap, sent with it a cd with drivers. I get the message when I double-click the install.exe or autorun.exe. So what you are saying is that the drivers are not working with linux and I should do........what?

---

### Post by bjauk on 2006-12-20
hmmm...when I enter the device manager, it doesn't seem like ubuntu recognizes the computer at all.....

---

### Post by Swab on 2006-12-20
> **bjauk said:**
> It's not easy to say if it works fine, since I don't have anything running on it. Had some problems with 1st boot after install, where it seemed to freeze up. I shut it off and the same thing happened. The third time, I applied the live-cd (from where I installed) and then it started perfectly (meaning started the installed version and not the live one). The company that buildt the lap, sent with it a cd with drivers. I get the message when I double-click the install.exe or autorun.exe. So what you are saying is that the drivers are not working with linux and I should do........what?

When you boot up without the live CD, at what point does it freeze?

---

### Post by Swab on 2006-12-20
> **bjauk said:**
>  So what you are saying is that the drivers are not working with linux and I should do........what?

Yes, those drivers are for Windows only.  Unfortunately some hardware manufacturers don't support Linux, and won't even open up their specifications to let other people make drivers.

When you boot with the Live CD,  Try opening a terminal (applications>accessories>terminal) and typing the following:

sudo su <enter>
lshw <enter>

Then copy and paste the results back to here.  It should give us an idea of the hardware you are working with.

---

