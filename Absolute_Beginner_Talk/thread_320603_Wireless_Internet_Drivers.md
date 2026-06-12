---
title: "Wireless Internet Drivers"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by jamaxus on 2006-12-17
ok, my problem is getting my wireless internet drivers installed so i can get onto internet in ubuntu otherwise its pointless and a waste of time dispite the fact i want to move away from windows. First off im using a safe com swlut-54125 wireless internet adaptor 54mps. 

I need to know how to install the drivers. i have them sitting in ubuntu but the application add/uninstall thing dosent pick it up and out of the 3 diffrent run files i cant run any of them... what do i do?

---

### Post by kane77 on 2006-12-17
what run files are they? (.sh?)

---

### Post by jamaxus on 2006-12-17
ok well first theres a .exe one which confused me as i thought that was windows only... but there is also setup files labeld .inx Theres also a file named ikernel. anyway you can download them here: [http://safecom.cn/code/support/DMF.aspx?pid=321](http://safecom.cn/code/support/DMF.aspx?pid=321) if you want a look first hand, however they are not the exact version of drivers but it says they should work.

---

### Post by jamaxus on 2006-12-17
bump.... anyone know or can find out? please post even if your just doing tests...

---

### Post by houstonbofh on 2006-12-17
Best I can tell it is a zd1211 based card.  3 USB adapters based on this chipset work out of the box in Ubuntu.  You may not need a driver.  What problems are you having?

---

### Post by msak007 on 2006-12-17
Based on what I've found [here]("http://acx100.sourceforge.net/matrix.html"), it's actually a Texas Instruments based chipset (tnetw1450). There's a project for the drivers called "acx100" which seems to encompass all the TI based chipsets. I don't know much about the chipset, but [this]("http://www.ubuntuforums.org/showthread.php?t=233565") thread may help you. It's not specific to a Linksys card because it's using the acx driver, but it's based on Dapper so I'm not sure how different it'll be in Edgy. When you plug your adapter into your USB port, what does the output of 
```
lsusb
```show?

---

### Post by jamaxus on 2006-12-18
ok well ill give a proper look to all the threads linked and try to answer your questions but i have to go now... if anyone else has any more to add ird be glad to hear it.

---

