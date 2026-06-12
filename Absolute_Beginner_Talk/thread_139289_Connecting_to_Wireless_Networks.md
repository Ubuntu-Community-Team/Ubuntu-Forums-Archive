---
title: "Connecting to Wireless Networks"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by LycoLoco on 2006-03-03
After installing Ubuntu 5.10 on an old 400mhz laptop my girlfriend had, I have gotten Ubuntu (using Gnome) to recognize the USB Wireless Adapter that I have (Hawking HWU54G, Rev Z1), and I can see the SSIDs of everyone in her apartment complex, including her own router, but I can't seem to actually connect to them. Should I be looking for some kind of confirmation telling me that I've gotten an active connection? Any other ideas for why this wouldn't be working? The network is currently unsecured, to remove that as a possible roadblock. Thanks in advance.

Edit: Rebooting did nothing. The connection is active and sees the SSID, but using DHCP does nothing.

---

### Post by Q4U on 2006-03-03
From a noob... try using iwconfig.

For more info, check the section 4.3 of the Wireless Troubleshooting Howto:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29#head-ccf9f7b4d2a864b3c4413c6450b1c10709ccb2bf](https://wiki.ubuntu.com/WirelessTroubleshootingGuide?highlight=%28wireless%29#head-ccf9f7b4d2a864b3c4413c6450b1c10709ccb2bf)

Hope this helps. Q4U

---

### Post by gtkourounis on 2006-03-03
and again from a noob... try using > sudo dhclient the real experts on networking are in the networking area though, so you might get some answers there. i am having a complex problem with my wireless and thats where i got my answers. hope you find a solution.

---

### Post by LycoLoco on 2006-03-03
I guess I should have said that I've tried using sudo dhclient. Using wlan0, it goes through the whole DHCPDISCOVER deal, and at the end says 
```
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

If I run iwconfig, I get the following for wlan0
```
802.11b/g NIC  ESSID:"Mina's"
Mode: Master   Frequency=2.412 GHz  Access Point 00:0E:3B:02:AA:9D
Bit Rate: 1Mb/s
Retry:off  RTS thr=2432 B  Fragment thr:off
Power Management:off
Link Quality=4/92  Signal level=20/154  Noise level=161/154
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0
```

Finally, running ```
sudo iwconfig wlan0 essid mina's ap 00:0E:3B:02:AA:9D mode Master commit
``` gives the following:
```
Error for wireless request "Set AP Address" (8B14):
SET failed on device wlan0 ; Operation not supported
```

Hope this helps in understanding what's going on. Thanks for the help thus far Q4U.

---

### Post by Q4U on 2006-03-03
At least we know your driver seem to work allright.

It might be a problem with the card which start to go into scanning mode automatically: check this thread out, I got the feeling you might have the same problem of this guy (see if you can solve it with the little script he did): [http://bbs.archlinux.org/viewtopic.php?t=5515&view=next&sid=aadc094631f4ac70eb323830cec5ed42](http://bbs.archlinux.org/viewtopic.php?t=5515&view=next&sid=aadc094631f4ac70eb323830cec5ed42)

Q4U

---

### Post by LycoLoco on 2006-03-04
Well, something worked right at our LAN party, I'm not sure what, but we got it online. Today, I can't seem to replicate the results. Anyone have any ideas for me?

---

