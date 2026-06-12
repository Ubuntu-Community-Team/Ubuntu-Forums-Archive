---
title: "MacBook Pro 3.1 Very Weak Wireless Performance Using Jaunty"
date: 2009-04-17
forum: Apple Hardware Users
---

### Post by kjano on 2009-04-17
Hi,

I updated to jaunty yesterday and want to report on wifi problems. running newer atheros chips with ubuntu was always difficult but IMO intrepid and ath9k solved these kind of issues more or less. surprisingly they are back in jaunty (rc1) now. my connection is very weak which especially affects surfing, in fact you always have to reload a page several times to get it working. the connection always stops for some seconds (!) before it works again, see ping example below. maybe this corresponds to the comment on another bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/342802/comments/5](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/342802/comments/5) (however in my case it only disconnects very rarely).

ping example:
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=175 ttl=250 time=42.7 ms
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=176 ttl=250 time=39.2 ms
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=177 ttl=250 time=42.5 ms
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=221 ttl=250 time=**5413 ms**
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=222 ttl=250 time=4414 ms
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=223 ttl=250 time=3407 ms
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=224 ttl=250 time=2407 ms
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=225 ttl=250 time=1409 ms
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=226 ttl=250 time=403 ms
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=227 ttl=250 time=42.5 ms
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=228 ttl=250 time=41.6 ms
64 bytes from [www.heise.de](www.heise.de) (193.99.144.85): icmp_seq=229 ttl=250 time=42.0 ms

i was using ndiswrapper in 8.04 but ath9k since 8.10.

modprobe wl results in:
...@simbox:~$ sudo modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/mactel-support-srosa-sound-fix, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/mactel-support-fnmode-fix, it will be ignored in a future release.

lscpi:
0b:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

dmesg:
...
[ 16.911078] ath9k: 0.1
[ 16.911120] ath9k 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 16.911131] ath9k 0000:0b:00.0: setting latency timer to 64
[ 17.038580] phy0: Selected rate control algorithm 'ath9k_rate_control'
[ 17.077654] Registered led device: ath9k-phy0:radio
[ 17.077670] Registered led device: ath9k-phy0:assoc
[ 17.077682] Registered led device: ath9k-phy0:tx
[ 17.077696] Registered led device: ath9k-phy0:rx
[ 17.078037] phy0: Atheros 5416: mem=0xffffc200043c0000, irq=16
...


i also created a bug report for this issue. ansy ideas? solutions? hints? :D

---

### Post by cyberdork33 on 2009-04-17
> **kjano said:**
>  i also created a bug report for this issue. ansy ideas? solutions? hints? :D
can you link to your new bug report?

---

### Post by kjano on 2009-04-18
yes, but there is no answer yet [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/362985](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/362985) . the connection really stops transmitting any data for about 10-15 seconds, than works again for some time (seconds) and than stops again fpr 10-15 seconds. this makes wifi nearly useless :( and 11n does not connect at all, i have to use 11g.

---

### Post by david_edmundson on 2009-04-18
I have this too. I'm getting disassociated with the Wireless point.

dmesg output (just grabbed a small section, this repeats a lot):

[   24.098943] wlan0: RX AssocResp from 00:17:3f:10:b0:28 (capab=0x421 status=0 aid=1)                 
[   24.098945] wlan0: associated                                                                       
[   24.120126] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                      
[   24.120229] wlan0: disassociating by local choice (reason=3)                                        
[   34.680053] wlan0: no IPv6 routers present                                                          
[  293.675236] wlan0: direct probe to AP 00:17:3f:10:b0:28 try 1                                       
[  293.679375] wlan0: authenticate with AP 00:21:04:16:47:27                                           
[  293.679440] wlan0: authenticate with AP 00:21:04:16:47:27                                           
[  293.877079] wlan0: authenticate with AP 00:21:04:16:47:27                                           
[  294.077068] wlan0: authenticate with AP 00:21:04:16:47:27                                           
[  294.276113] wlan0: authentication with AP 00:21:04:16:47:27 timed out                               
[  315.059642] wlan0: authenticate with AP 00:21:04:16:47:27

---

### Post by david_edmundson on 2009-04-18
Good news! linux-backports-modules-jaunty. seems to have fixed it for me. Though I can't see anything relevant in the changelog... weird.

---

### Post by kjano on 2009-04-18
yes

linux-backports-modules-jaunty
wicd

fixed it for me.

---

### Post by tikibaloni on 2009-05-31
Even after linux-backports-modules-jaunty, the signal is not optimal Is there any other way?

---

### Post by tikibaloni on 2009-06-01
wicd doesn't seem to make a difference.

---

### Post by dman777 on 2009-06-03
You are most likely using the wrong driver for that card. I had the same problem using the wrong driver for a broadcom card. It worked, but really bad. 

 What you need to do is find someone with a Windows machine with that EXACT card. Then, get thier .inf file and load it into your ndis wrapper.

---

