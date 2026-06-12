---
title: "Wireless Help With D-Link DWL-650"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by JoeNobody on 2006-10-28
I am this -> ](*,) 

I have a D-Link DWL-650 card. Been trying for 2 days now getting it installed with Ubuntu 6.10. 

I installed NDISwrapper through Automatix... it took a while but I found the RealTek driver and now it detects hardware through it. The direct D-Link dirver for the card didn't work only the RealTek one. Here are my outputs.

lspci
```
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
```

ndiswrapper -l
```
Installed ndis drivers:
net8180 driver present, hardware present 

```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b link..  ESSID:"TheHole"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Sensitivity=80/85  
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=91/100  Signal level=-53 dBm  Noise level=-247 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

When I goto Connection Properties I have eth0 and lo listed, not wlan0. When I manually type in wlan0, I can see the signal strength bar but it says Disconnected. 

I goto properties of my card I enter my wireless network name, TheHole, and enter my WEP key as Hexadecimal... PLain doesnt work either. I have Activity light blinking but never the Link light.

There is something stupid I am missing because everything points to that I have the card installed and it is being detected. I have posted this on a few board to no avail with any help other than list command outputs... So I posted everything here. 

What am I missing???

---

### Post by thornomad on 2006-10-28
I know this is not the kind of advice you want to hear ... however, I had a DWL-650 and gave it up (sold it on eBay) for a DWL-650+ ... with the DWL-650+ there is no additional installation necessary on either Dapper or Edgy.  Both work plug-and-play.

I never got my 650 to work.  Went with the 650+ (different chipset).

---

### Post by JoeNobody on 2006-10-28
Thats fine, I have about 30 min before I run to the store and get a plug and play one. Thats fine. The 650 is almost 4 years old anyway and those who did get it to work, they could only get 11 mbps.

Oh well.

The 650+ can I still get it at stores? What latest and greatest cards are plug and play with 6.10.

---

### Post by gn2 on 2006-10-28
> **JoeNobody said:**
> Thats fine, I have about 30 min before I run to the store and get a plug and play one. Thats fine. The 650 is almost 4 years old anyway and those who did get it to work, they could only get 11 mbps.

Oh well.

The 650+ can I still get it at stores? What latest and greatest cards are plug and play with 6.10.

The DWL-650 ia an 11mbps card, superseded by the DWL-650+ 22mbps card (which I have) It uses the ACX 100 chipset from Texas Instruments and is plug & play in Ubuntu 5.10 and 6.06. I haven't tried 6.10 yet, but see no reason why it shouldn't be OK.

Faster DWL-650+ 54mbps cards are available in stores now, but if it's just internet access the 22mbps card's fine, although it would be second hand on eBay where I got mine for £7.00 (UK sterling)

You can always sell the DWL-650 on eBay to offset the cost?

---

