---
title: "BCMWL5 wifi card, Hardware Not Present"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by JamesBonz on 2006-11-04
Okay, I've read every site, used every guide, even wen't to the irc channel (it was very busy so I did't get much information).

My system is an eMachine M6809 laptop with a Broadcom Wifi card.

lspci | grep Broadcom\ Corporation
0000:02:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

My problem is, I have ndiswrapper installed, I have NTFS read support too (so I could retrive my wifi cards driver straight from my windows partition). I ndiswrappered my driver BCMWL5.inf

ndiswrapper -l
Installed ndis drivers:
bcmwl5   invalid driver!
bcmwl5a  invalid driver!

and in the 'Wireless Network Drivers' program (system -> Administration -> Wireless Network Drivers) it says:

bcmwl5
Hardware present: No
bcmwl5a
Hardware present: No

Like I said, I've tried every guide and im stumped.

Any help would be greatly appriciated.

Thanks in advance.

~JamesBonz

*update, I've tried the newest drivers, not just the ones that I took from my NTFS harddrive
because a friend thought ndiswrapper belived it was an invalid version, but it still did't work.

---

### Post by JamesBonz on 2006-11-08
Bump.

---

### Post by jeffster1970 on 2006-11-08
You may want to 'google' bcm43xx and find out what other brands used this style of chip. You may get away using a totally different driver..as long as it is a 'bcm43xx'  My card is a Microsoft 720MN...as well as a 'bcm43xx'.  Although the Linux driver is **supposed** to run this card..it didn't.  Go hunting for drivers such as mine, download them into your home directory.  Go into your terminal and completely uninstall the ndiswrapper and reinstall then re-try with the new driver.  This won't affect the windows install if you have one.  If you want..you can try this site as well: [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)  Anyway..good luck.

---

