---
title: "dual boot problems"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by trelka on 2008-03-22
I have been trying for four hours to create a dual boot system with an Ubuntu 7.04 installation CD on a Gateway T-1625 notebook with an ATI radeon graphics card.  I continue to get the same error message on the order of "no screens detected", and than am instructed to reconfigure the X server.  I have been into the x server reconfigurator and chose "ATI" and "Vesa" drivers with continued failure to go through the rest of the boot process.  I have even downloaded the "fglrx" driver while prompted after the x server finishes up, but it is never a choice in the x server drivers listing after rebooting.  I love ubuntu and bought this computer specifically for the dual boot capability and forgot about the caveats of ATI radeon cards. 

Is there any way to continue through the rest of the installation process so that all I have to do is download the proper drivers from the synaptic package manager?  If not, what can I do from the installation process?

PLease someone help me.

Darin Trelka

---

### Post by manishtech on 2008-03-22
ATI Raedon graphics cards are a real headache for linux Xserver, we faced a lot of problems while organizing Install fest in our college due to ATI

Just get an alternate CD of Ubuntu (this is what we did). This alternate CD does not have a graphical install but a text based install, after you installed it, you can configure the Xserver.

Ubuntu is ultimate, i feel pity that due to bugs of ATI drivers, the problem is faced by people who want to try Ubuntu.... 

Am not sure whether ATI drivers are restricted....

---

### Post by jan quark on 2008-03-22
here is good guide for the alternate installation:
[LIST]
[*][http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
[/LIST]

---

### Post by defrex on 2008-03-22
Also, using 7.10 might work better then 7.04. Each new version of Ubuntu seems to get better at handling these type of issues.

---

