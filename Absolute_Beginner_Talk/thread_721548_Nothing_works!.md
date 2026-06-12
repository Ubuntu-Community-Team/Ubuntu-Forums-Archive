---
title: "Nothing works!"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by beng165 on 2008-03-11
Hi,

I have a Dell Inspiron 1520 with windows vista, but I was getting tired with the constant bluescreening so i decided to install ubuntu 7.10. Everything worked fine during the installation, but I've found that alot of the stuff doesnt work yet. For example, I cant increase the visual effects, sound doesnt work, and neither does wireless. 

I searched a few forums for answers but to be honest I find these REALLY confusing. If you can help me, I'd advise you to use small words:)

Spec:Base
	Intel® Core&#153; 2 Duo Processor T7250 (2.00 GHz, 2 MB L2 cache, 800 MHz FSB)
Memory
	2048MB 667MHz Dual Channel DDR2 SDRAM [2x1024]
Video Card
	Integrated Intel® Graphic Media Accelerator X3100
Hard Drive
	160GB (5400RPM) SATA Hard Drive
Modem
	56.6k V.92 Capable Internal Modem & Adapter - UK
Optical Devices
	Fixed Internal 8X DVD+/-RW Drive including Software
Wireless Networking
	Intel® Pro Wireless 3945 802.11a/b/g Mini-Card - Europe
Bluetooth
	Dell&#153; Wireless 355 Bluetooth 2.0 Module (up to 3Mbps) with Enhanced Data rate - Eur

Many thanks, Ben

---

### Post by ugm6hr on 2008-03-11
Perhaps you could start by explaining how you have tried to get stuff working.

As a starter - I would suggest 1 thread per problem, or ask 1 question at a time, cos it can get confusing otherwise.

Anyway:

1. Wifi

Your Intel wifi card should just work.  The driver should be installed automatically at the time of installation.  You can check with the following command (all commands are case sensitive):
```
lshw -C network
```
This should have a line with *driver=xxx* that confirms the driver.  Post the output here if you want us to check.

If the driver is installed correctly, then the other issue is likely to be your encryption.  What type do you use?  WEP/WPA etc / MAC filtering / hidden SSID?

Another command that may be useful is:
```
iwconfig
```

2. Sound

You haven't said what sound card you have!

The following command will be useful to give that info (post here):
```
lshw -C sound
```

If the driver has been installed (which is likely to have happened automatically), then it is often a case of changing the volume on different channels.

This command will allow you to adjust volumes (use Tab, Arrow keys and M button)
```
alsamixer
```

3. Visual effects

What effects are you looking for?  Compiz-Fusion is likely already on.

What setting do you use on System-> Preferences-> Appearance-> Visual Effects tab?

If you try choosing anything other than None, what happens?

---

### Post by Oldsoldier2003 on 2008-03-11
I agree with ugm6hr a thread per post makes it less confusing. Also... from past experience might I suggest picking one problem to fix at a time?It makes it a  lot easier and less likely to result in mucking something up by accident.

---

