---
title: "Can't get wireless to work.  Help plz."
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
and following are results.

(I've tried to install 'network manager' as lots of ppl seem to be using it,
 but in add/remove section of Ubuntu it says it cannot be installed in my
 computer type(i386). 
 I don't have internet connection with my ubuntu, but I don't think that's
 the problem here, other application doesn't say this.
 but mine is just regular labtop PC with intel pro/wireless chip(centrino)
 Upper-right coner of panel, I see an network icon and it's network monitor
 I guess this is network manager like application.. it came with installation.)

And I have WEP encryption on my router(linksys G)

  





Result of 'iwlist eth1 scan'

'Cell 03 - Address: 00:13:10:A0:16:66
ESSID:"Danny"
Protocol:IEEE 802.11bg
Mode:Master
Channel:6
Encryption keyn
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 48 Mb/s; 54 Mb/s
Quality:84 Signal level:0 Noise level:0 Extra: Last beacon: 704ms ago




Result of ' iwconfig'

'lo no wireless extensions.

eth0 no wireless extensions.

eth1 unassociated ESSID:"danny"
Nickname:"ipw2100"
Mode:Managed Channel=0
Access Point: Not-Associated
Bit Rate=0 kb/s Tx-Power:16 dBm
Retry min limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.



Result of ' lshp '


*-network:1
description: Wireless interface
product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
vendor: Iantel Corporation physical id: 7
bus info: pci@02:07.0 logical name: eth1 version: 04 serial: 00:0c:f1:2e:2c:65
width: 32 bits clock: 33MHz capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2100 multicast=yes wirele


I appreciate any help in advance.

(Going little crazy here to tell you the truth, but enjoyin ubuntu at the
same time ! )

(I've reposted this msg, cuz the original is far down due to high post volume
 of this forum, if this is not ok, let me know.)

---

### Post by skale on 2007-02-28
Did you try running `dhclient` in the terminal?

I can't remember if it is `dhclient` or  `dhcpcd` that Ubuntu uses.  I am fairly sure it is dhclient.  

I have the same chip, and it should work hassle-free, and it seems to work (based on a cursory look of your output), so I think just running `dhclient` will work just fine.  Without the `s of course.

---

