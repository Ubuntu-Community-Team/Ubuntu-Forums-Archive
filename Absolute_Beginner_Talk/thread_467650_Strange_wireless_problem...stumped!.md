---
title: "Strange wireless problem...stumped!"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by doctorproteus on 2007-06-07
I loaded edgy about a month ago, and wireless set up on my HP dv9000 with internal antenna just fine on the first try.  I then took a trip to Maryland and tried to tap into mother's router and couldn't get it to connect.  Got busy and didn't try to troubleshoot then.  I have come back home and now cant connect here either.  Belkin router shows that my mac address for laptop is a DHCP client, and laptop shows ip address assigned when I run ifconfig.  I have a light that tells me when the computer is in wireless range and receiving a signal, but it is not coming on.  My ->administrator->network settings are right and I am showing no signal strength on eth1.  Should it be set to wlan0?  I believe it used to be.  Anyway, I would be happy to post any settings if you tell me how to stop the madness!!!

---

### Post by doctorproteus on 2007-06-07
iwconfig shows

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: 00:C0:A8:8E:6D:92   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12827   Missed beacon:0

sit0      no wireless extensions.

---

### Post by kill4killin on 2007-06-07
which version of network manager are you using?

have you tried doing

```
sudo iwconfig eth1 essid *your essid*
```

---

### Post by doctorproteus on 2007-06-07
Not sure how to figure out version of network mangager, but whichever came with edgy 6.10.  I have tried your other suggestion per the wireless network troubleshooting guide.  Thank you for your help.

---

