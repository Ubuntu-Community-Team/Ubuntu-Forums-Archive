---
title: "Even after ATI Sticky, still no X server"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by ial7672 on 2007-06-17
I followed the Sticky:  Installing Ubuntu 7.04: ATI X**** Cards above, and after reboot got:


Failure to start X server...
(WW) Fglrx: no matching device section for instance (BUSID PCI:1:14:1)
(EE) No devices detected

Fatal Server Error:  No screens found

Then I get a message stating:

X Server Disabled . . .

I am a newbie and need help.  I am using an ATI Radeon 9200 and the computer also has an Intel video card that came with the computer that I am not using.

Thanks.

---

### Post by w4ett on 2007-06-17
You should be using the Open Source ATI driver.  Open a terminal and enter the command:

sudo dpkg-reconfigure xserver-xorg

In the Semi-Graphical interface select the driver ATI and also your correct Resoultiona & Refresh rates for your monitor.

Save your selections.

Restart X by using <Ctrl><ALT><Backspace>

You should be able to log into your desktop

---

### Post by ial7672 on 2007-06-17
Thanks for the help.  It worked.  I had to find the PCI bus information, and did so using lspci.
Besides that, the procedure you provided worked perfectly.

Thanks!:popcorn:

---

### Post by w4ett on 2007-06-17
No Problem....Welcome to the club!

---

