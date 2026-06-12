---
title: "New to Linux (wireless help)"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by maig on 2007-12-06
Hi newb question here, but how do you configure Ubuntu 7.10 took work with wireless?

---

### Post by daimaru on 2007-12-06
if you click your top panel's wireless connection thing you should see all available wireless networks. click yours enter credentials and your good to go. if not you should post the output of the following commands (in the terminal "accessories-->terminal")
```
ifconfig
```
```
iwconfig
```
and the wireless card your using if its pci post output of
```
lspci
```

---

### Post by maig on 2007-12-06
> dixon@Galileo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:38:5E:ED:EA  
          inet addr:192.168.1.89  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe5e:edea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6709 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6895674 (6.5 MB)  TX bytes:957467 (935.0 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

dixon@Galileo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

dixon@Galileo:~$ ifconfig
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)


I'm starting to think my wireless might not be supported.

---

### Post by daimaru on 2007-12-06
no idea if this will help you , but it seems people are having trouble with that card. 

> A quick howto for how I got my Atheros AR5007EG WLAN card working in Gutsy:

1. Install ndiswrapper. (sudo apt-get install ndiswrapper) You can also install ndisgtk to get a graphical interface for this. (sudo apt-get install ndisgtk)

2. Download [http://blakecmartin.googlepages.com/...er-0.1b.tar.gz]("http://blakecmartin.googlepages.com/atheros-ar5007eg-installer-0.1b.tar.gz") However, you only need the .inf-file that is inside (I believe it's called net5211.inf)

3. Install the .inf file in ndiswrapper, either with ndisgtk or the command "sudo ndiswrapper-i net5211.inf"

4. Disable the ath_pci module in the restricted manager.

5. Reboot, and you should be fine

taken from somewhere...
 		
from this thread : [http://ubuntuforums.org/showthread.php?t=563587&page=2](http://ubuntuforums.org/showthread.php?t=563587&page=2)

---

### Post by maig on 2007-12-06
thanks!

---

### Post by daimaru on 2007-12-06
well i do  hope it works, but dont get ahead of yourself and dont sue me for anything that happens to your comp by following those instructions :)

---

