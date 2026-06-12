---
title: "Help with wireless connection... plz..."
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by waytorun on 2007-02-28
Hi, I just experienced lunux for the first time today, so please forgive me

for any 'noobness'. 


I have 'Sens X10 plus' from Saumsung. It's a labtop PC.

It seems that the pro/wireless ipw2100 b3 is detected by the system but

I can't get online. I think driver is loaded as well. But it's not associated with

the router(whatever assciation means in this context),


I was reading thru some stuff about ubuntu(man there are lot to read)

and came upon couple of commands.


I ran 'iwconfig', 'iwlist eth1 scan' and 'lshw', 

and  following are results.





Result of 'iwlist eth1 scan'

'Cell 03 - Address: 00:13:10:A0:16:66 
           ESSID:"Danny"
           Protocol:IEEE 802.11bg
           Mode:Master
           Channel:6
           Encryption key:on
           Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
           11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s  48 Mb/s; 54 Mb/s
           Quality:84  Signal level:0  Noise level:0   Extra: Last beacon: 704ms ago




Result of ' iwconfig' 

'lo  no wireless extensions.

 eth0  no wireless extensions.

 eth1  unassociated  ESSID:"danny" 
       Nickname:"ipw2100"
       Mode:Managed  Channel=0 
       Access Point: Not-Associated  
       Bit Rate=0 kb/s   Tx-Power:16 dBm 
       Retry min limit:7   RTS thr:off   Fragment thr:off
       Power Management:off
       Link Quality:0  Signal level:0  Noise level:0
       Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
       Tx excessive retries:0  Invalid misc:0   Missed beacon:0
       
 sit0  no wireless extensions.



Result of ' lshp '


*-network:1
  description: Wireless interface
  product: PRO/Wireless LAN 2100 3B Mini PCI Adapter 
  vendor: Iantel Corporation    physical id: 7
  bus info: pci@02:07.0 logical name: eth1  version: 04   serial: 00:0c:f1:2e:2c:65
  width: 32 bits   clock: 33MHz  capabilities: bus_master cap_list ethernet physical wireless
  configuration: broadcast=yes driver=ipw2100 multicast=yes wirele


I appreciate any help in advance.

(Going little crazy here to tell you the truth, but enjoyin ubuntu at the 
 same time ! :) )

---

### Post by zvezdogled on 2007-02-28
hi what kind of encryption do u have?

---

### Post by waytorun on 2007-02-28
> **zvezdogled said:**
> hi what kind of encryption do u have?


I have WEP encryption.

If this is not the answer you were expecting, let me know how I can

find out what you want to know.

Excuse my noobness, :) but I'm trying. 


Thank you for the reply BTW.

---

