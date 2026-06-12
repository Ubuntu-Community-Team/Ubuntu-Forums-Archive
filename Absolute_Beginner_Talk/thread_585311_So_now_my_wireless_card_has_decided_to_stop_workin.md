---
title: "So now my wireless card has decided to stop working"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Ulfursson on 2007-10-21
Long story short, I've turned the wireless switch on my laptop off to conserve power, and when I turned it back on, Ubuntu won't detect the wireless card anymore. What's wrong here? My wireless card is an Intel Wireless WLAN Link 4965AGN 802.11a/g/n

---

### Post by Pumalite on 2007-10-21
Wireless:


[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

---

### Post by Ulfursson on 2007-10-21
> **Pumalite said:**
> Wireless:


[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
[http://ubuntuforums.org/showthread.php?t=580376&page=3](http://ubuntuforums.org/showthread.php?t=580376&page=3)

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

I'm sorry, but all of those guides either refer to older ubuntu versions, or deal with the cases where the wireless card isn't detected in the first place. Mine was, but stopped working after I flipped the wireless switch and turned it back on.

---

### Post by Pumalite on 2007-10-21
At this time we are all in 'terra incognita'. I hope someone comes along with the solution.

---

### Post by jd65pl on 2007-10-21
I know others with dead intel wifi cards specifically

ipw3945

---

### Post by Ulfursson on 2007-10-21
Update: It appears that my wireless card is recognized:

```
eyjolf@ANDLANG:~$ lspci -v
#other stuff
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1101
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f8000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
#the rest of other stuff

```
However, it still doesn't show up under network manager. I'm currently on a wired connection.

---

### Post by Ulfursson on 2007-10-21
bump bump bump...

---

### Post by Ulfursson on 2007-10-21
another bump

---

### Post by Zipster90 on 2007-10-23
Seems like I'm having the same problem, but my wireless hasn't worked since I've installed Gutsy. It worked in the live CD, so I don't get it.

---

### Post by zubala on 2007-10-23
I had the same problem too in gutsy. i had installed ndiswrapper and then installed the wireless driver and my wireless worked.  but when i restarted my computer, i lost my wireless connection, the network manager didn't even offer a wireless option.  I followed one of pumalite's links: 

[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)

and it fixed my problem.

---

### Post by _oOMOo_ on 2007-10-23
> **Ulfursson said:**
> Update: It appears that my wireless card is recognized:


Hi Ulfursson what is the output of

```

ifconfig -a

```

cheers

---

### Post by rezorcinol on 2007-10-23
Hello, I have the same problem and my output of "ifconfig -a" is:

```

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1B:38:55:11:99
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe55:1199/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:55209655 (52.6 MB)  TX bytes:2688558 (2.5 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5807 (5.6 KB)  TX bytes:5807 (5.6 KB)

wlan0     Link encap:UNSPEC  HWaddr 00-13-E8-5F-18-1F-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:152561 (148.9 KB)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-5F-18-1F-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by _oOMOo_ on 2007-10-23
Ok so your interface is up, that's a good start. What is the output from:

```
sudo iwlist wlan0 scan
```

If your wireless network is listed in the result then you can try

```
sudo ifdown wlan0
```

followed by

```
sudo ifup wlan0
```

to reset the interface and test if network manager then sees (and possibly connects to) your network.

Do you know which chipset your card uses rezorcinal?

---

### Post by rezorcinol on 2007-10-24
Today I've turned on my laptop and network worked fine. I don't know where error was.

---

