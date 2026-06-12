---
title: "Trouble with Broadcom 4311"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by StormGuy on 2006-12-19
I'm having a terrible time getting my Broadcom 4311 card to work on my Gateway laptop.

I've tried several guides on the forums, namely [this]("http://www.ubuntuforums.org/showthread.php?t=25683") and [this]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")  . 

However, I still can't manage to set my card up properly.  I usually get to a point where it looks like it detects my card and gives me the following outputs:

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and iwlist wlan0 scan
```

opus@Serenity:~$ wlan0     No scan results

```

So...it looks like it should work to me, but it doesn't.  I believe those outputs correspond to steps 1 through six on the second guide I linked.  I can't manage to manipulate my essid or scan with my wireless card at all.  

However, right now, after messing around with the config files in /etc/network/interfaces and /etc/iftab according to Totoro's post in [here]("http://ubuntuforums.org/showthread.php?t=201902&page=4") , my output now reads like this:

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:E0:B8:B9:6F:50  
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:feb9:6f50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2044695 (1.9 MiB)  TX bytes:307132 (299.9 KiB)
          Interrupt:217 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

```

and iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

I'm afraid to say that I'm at my wits end ](*,) .  Any help would be appreciated.

---

### Post by StormGuy on 2006-12-19
I tried to use a different wireless card just now (a D-link Air Plus DWL-650+) and the icon for my network manager changes to the familiar (for me) picture of a computer monitor with a warning sign and a nearly empty meter next to it.  So, it looks like it's detecting this card just as well as it detected my Broadcom card.  I don't think these cards are both giving me the same issue, rather, I think there must be something I misunderstood that I need to configure somewhere?  Am I wrong?  Any thoughts?

Edit: I used the ifconfig wlan0 down and then ifconfig wlan0 up commands and suddenly the meter is green...but the warning sign is still there and I don't have net access.  The card is actually scanning, though, and the signal strength is reading at 90+ percent :)

I'll take whatever little victories I can get at this point.

---

### Post by StormGuy on 2006-12-19
Success! I has an internet!  It's weird, though...it doesn't like WEP keys.  I read somewhere, I think, that you had to either input the key in hex or put some prefix at the beginning of the key to let it know you were using base 10.  I may be imagining things.  

In any event, huzzah :)

---

### Post by haiku99 on 2006-12-30
I've found that the network tool does weird things to the WEP key, in my case it puts -s before the key...so I try to avoid it now if possible and instead manually edit the config file by typing
sudo gedit /etc/network/interfaces
checking the file out is a good idea in any case, you can see what the configuration REALLY is....the network tool is often misleading IMHO

---

