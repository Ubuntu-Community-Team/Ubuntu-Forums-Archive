---
title: "[SOLVED] connecting with wireless"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-15
In system>admin>network i have 3 options wireless,wired,modem.  I have wired working fine, i have it on roaming mode then go to terminal and type: pon dsl-provider  .  Now this is where it gets tricky, i don't have a wireless router but there are plenty of signals in the area and a few that aren't secured.  i'm not 100% sure on how to connect to a wireless signal, 
when i put it on roaming mode i can't choose the signal i want to connect to, is there a terminal command to connect with?  and if so how do i choose which signal?  
when roaming mode is off i can choose a signal, which is unsecured, then put it as DHCP but i get nothing, again do i need to activate it with a terminal command?

here is the out put for iwconfig and the signal i wish to connect to:
> 
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=150 Mb/s   
          Fragment thr=1500000 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> 
 
Cell 01 - Address: 00:06:25:76:52:ED
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


Thanks, Alain

---

### Post by rjfioravanti on 2007-07-15
Try this

the first line is to associate, the second line is to get IP via DHCP

```

sudo iwconfig wlan0 essid linksys
sudo dhclient wlan0

```

---

### Post by ukripper on 2007-07-15
Try kde app called wlassistant it wil detect most of the networks around amazingly even XP never used to detect for me.

```
sudo apt-get install wlassistant
```

if you got gnome then you can run it from CLI

sudo wlassistant

---

### Post by S15_88 on 2007-07-15
thanks rjfioravanti, that did the trick!  i think i'll stick with using the termianl to find connections, i jus wanted to make sure my wireless worked 100% because next year at universirty we have a 5GB upload/5GB download with our wired connection but they don't track the wireless so i'll have to settle with using wireless to downloaded stuff, i hear it's still decently fast though.  thanks for the help!

---

