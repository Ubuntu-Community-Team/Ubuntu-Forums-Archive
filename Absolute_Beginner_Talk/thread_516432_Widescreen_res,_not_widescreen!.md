---
title: "Widescreen res, not widescreen!"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by aidan_47 on 2007-08-03
Hi guys,
at first i was having trouble getting my widescreen monitor's resolution to 1440x900, but now ive managed to do that (by changing the xorg.conf file). So everything appears how it should, except that the bottom of the screen is cut off, the only way i can see the bottom is if i move my mouse toward the lower part of the screen, then it will scroll down the screen. 

I just want my desktop to appear 1440x900 without any scrolling.

Thankyou for any help you can give.

---

### Post by frodon on 2007-08-03
Post your xorg.conf file, without it it will be hard to help.

Then tell us the exact name of your screen and if you know the horizontal and vertical refresh rates of your screen (should be in your screen manual).

---

### Post by aidan_47 on 2007-08-03
My xorg.conf file is attached (i had to change the filetype to .txt). My Monitor is a Samsung SyncMaster940BW (thats 19inch widescreen). 

Horizontal refresh rates: 30-81khz
Vertical refresh rates: 56-75hz

Heres a page of the monitor and its specs if ya want [http://www.samsung.com/ca/products/monitor/lcd_digital/ls19hawkbqxaa.asp?page=Specifications](http://www.samsung.com/ca/products/monitor/lcd_digital/ls19hawkbqxaa.asp?page=Specifications)

Thanks a lot.

---

### Post by frodon on 2007-08-03
From what i see your xorg.conf looks just fine, you even added the HorizSync and VertRefresh which often solve all resolution problems.
Each time i got this kind of behaviour it was after a game crash and restarting X put back the normal configuration.

You should have a look in the log viewer and watch the message, xorg.log and kern.log files seeking for errors or additional informations which might help to identify the nature of the problem.

---

### Post by pikul on 2007-08-03
Why don't you change your DefaultDepth from 16 to 24 ? it won't hurt to try :redface:

---

### Post by frodon on 2007-08-03
> **pikul said:**
> Why don't you change your DefaultDepth from 16 to 24 ? it won't hurt to try :redface:yes, i second this.

---

