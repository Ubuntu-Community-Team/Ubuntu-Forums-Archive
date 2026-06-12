---
title: "Wireless Networking - stumped"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by emp on 2006-12-31
Hmm.

I just installed Edgy Eft and it can't find my wireless router.

The card seems to be working Okay, with "wMaster0" and "wlan0" shwoing in the network manager.

However, I can not seem to get a connection to the internet.

DHCP is activated on the router.

Is there any way to "sniff" for available networks, like I do on WinXP "Show available networks"?

Oh, the card is compatible it is a D-Link Airplus G DWL-510.

Thank you for any pointers.

::emp::

---

### Post by emp on 2006-12-31
OK, to clear this up a little, I am doing a bit more research:

emp@mico:~$ ifconfig
wlan0     Protokoll:Ethernet  Hardware Adresse 00:13:46:8A:5B:20  
          inet6 Adresse: fe80::213:46ff:fe8a:5b20/64 Gültigkeitsbereich:Verbindung
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:1296 (1.2 KiB)
          Basisadresse:0x9000 

wmaster0  Protokoll:UNSPEC  Hardware Adresse 00-13-46-8A-5B-20-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Basisadresse:0x9000 

emp@mico:~$ iwconfig
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"koenigreich"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
eth0      no wireless extensions.

sit0      no wireless extensions.

Thanks,

::emp::

---

### Post by benuski on 2006-12-31
Maybe try a 
```
sudo iwconfig ethX ap any
```
That sometimes helps me out.

What I use for a packet sniffer to find available networks nearby is a program called kismet, which is avaiable in the repositories.  Its a little difficult to set up, but they have good documentation on their website.  There's another one called Wireshark, which I've never really used, and there are a few others in the repositories, I believe.  Hopefully you have wired access and can get one of these programs.

---

### Post by emp on 2006-12-31
Just connected my PC to the router via cable.
Am able to update/install the network manager now as well as another Wireless network management tool.

Hopefully this will solve  the problems.

Cheers, and a HAPPY NEW YEAR! :KS 

::emp::

---

