---
title: "Some Hardware problems"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by ParPelon on 2007-07-06
Hello everyboy :) 
first of all thanks a lot about all the information here, you`r great ! 

I have 2 problems with my hardware after i installed Ubuntu 7.04 +KDE 3.5 

the first one is with my TV adapter .
I`m using  AVerMedia AverTV Go 007 Fm Plus.
acording [http://linuxtv.org/v4lwiki/index.php/Avermedia_AVerTV_GO_007_FM](http://linuxtv.org/v4lwiki/index.php/Avermedia_AVerTV_GO_007_FM)  this adapter is "out of The Box".
In the device maneger the system found the adapter but i cant see nothing ! 
I really new on linux and i need installation guide or a link to something like that :) 

my secend broblem is with my bluetooth adapter . 
Im using Edimax USB Device Model EB-DGC2 . 
acording Edimax offical [http://www.edimax.com/en/support_detail.php?pd_id=127&pl1_id=13&pl2_id=43](http://www.edimax.com/en/support_detail.php?pd_id=127&pl1_id=13&pl2_id=43)  
this Device support Linx .I need this Bluetooth connection be`coz Im using V270 Cordless Optical Notebook mouse . the funny thing is that my cell phone (Nokia) find the BT device but My BT device can find MY Cell phone or my mouse (after i add mouse address in the BT Menneger  under My KDE desktop) 

*thos 2 devices work fine under my WINDOWS XP  :) 

thanks

---

### Post by DBStevens on 2007-07-06
I can't help with the bluetooth issue, however if you provide the output from:

dmesg

and 

cat /etc/modprobe.d/bttv

I might be able to help you.

I have an older AVerMedia card, while the drivers always load the required information in one of the configuration files is frequently default information.

---

### Post by crispy_420 on 2007-07-24
What happens when you try to launch tvtive from command line?

---

