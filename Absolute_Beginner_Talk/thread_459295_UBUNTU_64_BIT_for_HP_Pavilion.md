---
title: "UBUNTU 64_BIT for HP Pavilion"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by slackmaster on 2007-05-30
Hello,

I'm relatively new to Linux.  I have worked with windows for years.  So I know about computers and OSs but not much about Linux.  
I tried to install the 64 bit Ubuntu live CD on my HP Pavilion 90005US.  My laptop has  an AMD Turion 64 X 2 processor with a 1.6GHz AMD Dual-Core TL-50 processor.  It also uses a NVIDIA GeForce Go 6150 graphic card.  
I speculate that Ubuntu will not run in live mode because it does not recognize the hardware or drivers on my machine, but I'm not sure.  How can I fix this problem?  Thanks ahead of time for any suggestions.

Slack

---

### Post by lamalex on 2007-05-30
What exactly ... is the problem. You never explicitly state what it is. I assume that the live won't boot? How far does it get? Does it go straight to windows? Check your bios for boot to cd.

---

### Post by slackmaster on 2007-06-04
Hello,

I will give you a more detailed description.  I'm trying to run Ubuntu live on my HP.  I tried the 32-bit version today.  After selecting start or install, a message appears:  bug # 81 found.  Afterwards as the kernal loads, all goes well except 5 firmware libraries fail to load.  I did not jot down the specific microcodes but if you need those I can get them.  After the kernal loads, the screen is shot through with lines superimposed over blue and black splotchy graphics which appear to slowly darken from the edges of the screen.  At this point I turn off the machine.
Neither the 32 bit or 64 bit versions will work on my HP.  Thanks for your time.  

Slackmaster.:D

---

### Post by jcaveman on 2007-06-06
During the startup at the option screen hit F6 and add the following parameters to bootup:

noapic irqpoll noirqdebug

This should fix some of the problems your having.  The firmware errors are probably from the Broadcom wireless card.  The liveCD tries to load the bcm43xx driver and that won't work with this card.  The Broadcom 4311 really needs to use the ndiswrapper driver and you'll have to manually configure that using Windows drivers.

See this page for some more help:

[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by slackmaster on 2007-06-06
Thanks,

I'll give your suggestions a try and see what happens.  Cheers!:p

---

### Post by slackmaster on 2007-06-17
Your tip worked.   Thanks.  The live 64 bit CD runs now.  I'm thinking of installing it permanently but it doesn't recognize my wireless card.  The link you provided explains how to deal with that though.  Cheers;)

---

