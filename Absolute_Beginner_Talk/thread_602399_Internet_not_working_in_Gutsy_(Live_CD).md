---
title: "Internet not working in Gutsy (Live CD)"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by mithun1217 on 2007-11-04
I was using Feisty until now, and yesterday, I downloaded Gutsy, formatted my Feisty partition and tried booting Live off the CD.  My internet doesn't seem to work after I enter my IP, Gateway and DNS addresses.  So then I tried booting Live off the Feisty CD, and Internet works like a charm after I enter the configuration information.  How do I make Internet work on Gutsy?  I don't want to actually install it until I'm sure that everything will work fine.  Or should I go back to Feisty?

---

### Post by bumanie on 2007-11-04
I am not using gutsy at present due to major bootloader problems that I have not sorted out yet. I however suspect your problem may be related to the ipv6 stack that has been introduced into gutsy. Disabling ipv6 may cure the problem. Refer to this site for help [http://www.lockergnome.com/nexus/linux/2007/10/24/ubuntu-gutsy-internet-help](http://www.lockergnome.com/nexus/linux/2007/10/24/ubuntu-gutsy-internet-help)
Just as a side issue, when M$ first released ipv6 for windoze, I no longer had internet access via windoze although it still worked in feisty. When this happened under M$, my ISP told me they could see my modem connected to the internet , but for some reason (that they could not pinpoint) the modem and windoze would not communicate with each other. I did a system restore pre ipv6 and all was fine.

PS: The above fix may not work for the live cd, but should work if you decide to install gutsy onto your hard drive.

---

