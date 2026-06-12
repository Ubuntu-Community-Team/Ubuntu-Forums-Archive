---
title: "Realtak 8139"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by rtfmviolator on 2006-05-30
I just reloaded Ubuntu 5.10 and upgraded to 6.06. Dapper seems to have resolved a lot of problems I was having. This is a wireless laptop. An HP zv5000 with onboard Realtek 8139 wireless ethernet. Previously a friend of mine installed ndiswrapper manually and got wireless to work using Linksys 54G PCMCIA Windows driver. Strange. Anywho, I downloaded the XP driver RTNICXP.sys and tried to set up my wireless onboard card I'm such a newbie with Linux any instructions I try doesn't seem to work. But somehow I think I installed the driver with ndiswrapper -i rtnicxp.sys and hitting enter. I've put everything in for my router to include the WEP code but I can't activate the driver. Any help would be appreciated. I'm really green here and am pretty frusrated. Been a Windblows user for 11 years now, no novice, love the Linux feel though.

rtfm...

---

### Post by hw-tph on 2006-05-30
The Realtek 8139 network interface on the ZV5000/R3000z series is the *wired* interface. The wireless interface is a Broadcom 43xx series (usually BCM4306 but it differs between manufacturing dates) chip.

You can read about networking on the ZV5000/R3000z [here](http://prinsig.se/weekee/index.php/Networking_%28hw%29) and Ubuntu specific information (which probably is what you want) [here](http://prinsig.se/weekee/index.php/Ubuntu#Broadcom_WLAN). I think the instructions are pretty clear, if you disagree let me know what doesn't work for you.


Håkan

---

