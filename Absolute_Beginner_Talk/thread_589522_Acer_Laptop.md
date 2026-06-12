---
title: "Acer Laptop"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by rcdeacon on 2007-10-24
Does anyone have Gutsy installed on an Acer Aspire 5002 WLM1 laptop? I am considering a test run on my lappy now that I was able to get things sorted out on my Dell Dimension desktop. I am particularly interested in anyone who has been successful getting the broadcom 4318 airforce one wireless adapter to work consistently in Gutsy.

---

### Post by realvz on 2007-10-24
i have acer 5920  working without any issues...but i dont seem to have a broadcom card...

---

### Post by hyper_ch on 2007-10-24
Try the desktop cd and test yourself ;)

---

### Post by rcdeacon on 2007-10-24
I actually did run the live cd but I did NOT get a wireless connection. I did see the sticky regarding the "easy" way to get the broadom 4318 to connect but was unable to try it live.

---

### Post by realvz on 2007-10-24
maybe try this
[http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)

---

### Post by Tau_Lepton on 2007-11-19
I too have the 5002WLMi.  I did have wireless working in Feisty with ndiswrapper.  Installing it was fine, everything worked great.  Wireless broke when I upgraded to Gutsy, though.  I'm not sure exactly what happened, but it appears that ndiswrapper is still installed and working but the wireless button broke.  It seems that the switch was controlled by acerhk, which also seems to be working fine.  Basically, you need to have acerhk installed for the wireless switch and then follow the instructions that realvz posted for ndiswrapper.  Best of luck!

---

### Post by Tau_Lepton on 2007-11-19
Well, I just got mine to work.  I just needed to re-add the line 'acerhk' to /etc/modules. For some reason loading the module manually didn't work -- is that normal?  Anyway, the acerhk + ndiswrapper approach seems to work well in Gutsy. :)

---

