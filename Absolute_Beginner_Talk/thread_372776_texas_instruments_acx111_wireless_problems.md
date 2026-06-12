---
title: "texas instruments acx111 wireless problems"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by rdh on 2007-02-28
I have set up ubuntu 6.06 on a 850MHz duron pc - no problems at all, dual booting with winxp. Everything is great except for my texas instruments pci acx111 wireless card. The card is recognised in the networking wndow, and I can input wep code etc. I have tried dchp and static address, manually inputting settings, but I cannot get online. I have checked that the card is recognised using lspci_-v_¦_less, and it is listed as 
Texas Instruments ACX111 54Mbps wireless interface
vendor: unknown
device: unknown
status:status
Bus type: unknown
device type: net.8021
capabillities: net,net.80211

I found a link from google, suggesting that I type the following:
 options acx firmware_ver=1.2.1.34

into           /etc/modprobe.d./options

I went to file browser and found the file? folder? /etc/modprobe.d./options, typed it in, but says i cannot save the changes. 
I know that the hardware is fine, as the card works fine with xp. 

I'm sure i've missed something fundamental, but I am truely stuck. Any help would be very appreciated! Thanks

PS i'm a total novice so you may have to spell things out!

---

