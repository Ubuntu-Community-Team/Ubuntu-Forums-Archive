---
title: "Network Troubleshooting -- wireless card won't enable"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by valkyrie on 2006-03-20
I installed kubuntu for the first time a few months ago, and everything was going swimmingly.  Then I did something very strange to a sound setting, did something even stranger with another package, and ended up needing to do a reinstall.  (Whoops :) )

Unfortunately, I don't remember the most complicated part of putting the system back in working order -- wireless card setup! I have a TrendNet wireless card with a Broadcom chipset, and so I have been following the instructions for ndiswrapper from this thread: [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

I *think* that the wireless card is working properly, but for some reason I can't enable the network interface.
[list][*]The wireless card's little green light is on -- it wasn't before ndiswrapper.  So, I think that I found the right *.inf file for ndiswrapper to use for this particular card.
[*]The Network Settings dialog shows two possible connections: eth0 (regular connection, and what I'm using right now), and wlan0 (the wireless card).  (Again, that makes me think that I've used ndiswrapper correctly.)
[*]Finally, KWiFiManager can find my home network and shows good signal strength.  (Although it does say "Local IP: unavailable")[/list]
Now this is where the trouble starts :(  I press "Enable Interface" in Network Settings, and it only enables for a couple seconds -- then it automatically disables again.  The device configuration is set to "Automatic: dhcp" and to activate when the computer starts.  I don't have any WEP key (bad, I know, but that's another thread entirely).

What really makes me wonder is that when the computer starts up, eth0 is normally enabled and wlan0 is disabled.  BUT -- If I unplug the ethernet cable, then restart the computer, both eth0 and wlan0 are disabled and can not be enabled.  eth0 works fine if it is plugged in during reboot, but wlan0 doesn't work whether eth0 is connected/enabled or not.

```
susan@ubuntu:/etc/ndiswrapper/bcmwl5$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:02:B3:05:62:B4
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:fe05:62b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2036681 (1.9 MiB)  TX bytes:336695 (328.8 KiB)

susan@ubuntu:/etc/ndiswrapper/bcmwl5$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:90:4B:1D:42:54
          inet6 addr: fe80::290:4bff:fe1d:4254/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:18400000-18401fff
```
I could, of course, be completely wrong -- maybe wlan0 is just totally screwed up :)

---

### Post by valkyrie on 2006-03-21
Browsed forum some more, found [http://www.ubuntuforums.org/showthread.php?t=126886](http://www.ubuntuforums.org/showthread.php?t=126886) and have now fixed problem completely.\\:D/

---

### Post by dvarsam on 2006-03-21
Hello !

Why don't you explain how you fixed it, share your personal experience, so that other users can learn from this (and hopefully fix their systems too)?

Thanks.

---

