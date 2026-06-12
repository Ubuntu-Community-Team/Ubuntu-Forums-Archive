---
title: "Cannot connect to internet"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by bluecaterpillar on 2007-03-05
Hi, I'm an absolute newbie running 6.10 - the Edgy Eft off LiveCD on a Thinkpad Z61t. My setup: wall-->Cable modem (Toshiba PCX2500)-->Wireless router (Buffalo Airstation WBR-G54)-->Thinkpad.

I can't connect to the internet (meaning, I can't open pages in Firefox or use Update Manager), either through the wireless or the ethernet connection. It doesn't even work when I connect the computer directly to the cable modem, so it's not just a problem with the router.

Ubuntu appears to detect the wireless card and thinks it's working, so I don't think this is a ndiswrapper issue ....

Here's the skinny:

ubuntu@ubuntu:~$ sudo pppoeconf
Interface ath0 has MTU of 1492 -- should be 1500.  You may have serious connection problems.

ubuntu@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"columbae"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:07:40:9F:5D:44   
          Bit Rate:54 Mb/s   Tx-Power:8 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:6368-6974-6865-7461-6368-6978-6F   Security mode:restricted
          Power Management:off
          Link Quality=53/94  Signal level=-42 dBm  Noise level=-95 dBm
          Rx invalid nwid:158216  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ubuntu@ubuntu:~$ sudo ifconfig
ath0      Link encap:Ethernet  HWaddr 00:19:7D:CB:4A:E9  
          inet6 addr: fe80::219:7dff:fecb:4ae9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80680 (78.7 KiB)  TX bytes:70270 (68.6 KiB)

eth0      Link encap:Ethernet  HWaddr 00:16:36:F1:3C:BF  
          inet6 addr: fe80::216:36ff:fef1:3cbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6604 (6.4 KiB)  TX bytes:0 (0.0 b)
          Interrupt:201 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-CB-4A-E9-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:259158 errors:0 dropped:0 overruns:0 frame:164536
          TX packets:1745 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:24213563 (23.0 MiB)  TX bytes:148872 (145.3 KiB)
          Interrupt:66 Memory:f8cc0000-f8cd0000 

Note: when I connect the cable modem directly to the thinkpad, it receives packets at a much faster rate.

   ...
eth0      Link encap:Ethernet  HWaddr 00:16:36:F1:3C:BF  
          inet6 addr: fe80::216:36ff:fef1:3cbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:905 errors:0 dropped:970 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64746 (63.2 KiB)  TX bytes:581952 (568.3 KiB)
          Interrupt:201 
   ...

Any help would be greatly appreciated!

---

### Post by Paul41 on 2007-03-05
See if this makes any difference.

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

---

### Post by bluecaterpillar on 2007-03-05
Hmm, it won't let me edit the /etc/modprobe.d/aliases file ... I assume because I'm running it off a CD and it's read-only?

Should I try running it from USB flash drive? Or do I need to bite the bullet and install it on the HDD?

---

### Post by Paul41 on 2007-03-06
OK, try this.  In the Firefox address bar type about:config.  on the screen that comes up filter for IPv6 and disable it.  This will only make the change for Firefox and not system wide, but it should let you know if this is the problem.

---

### Post by bluecaterpillar on 2007-03-06
Sending laptop into shop for unrelated hardware issue. Will try this method in ~1 week and post results. Thanks for your help!

---

### Post by bluecaterpillar on 2007-03-15
Hmm, I don't think it's the IPv6 - here's what popped up when I followed your instructions:

network.dns.disableIPv6     user set    boolean  false

I double-clicked it and the value became true.

Still no internet.

Incidentally, I opted for the Thinkpad branded wireless card instead of the Intel ProWireless ... could that be the problem? My instincts tell me no, since I'm able to configure the card from System>Administration>Networking. However, I *am* able to connect to the internet on my other computer, which *does* have the Intel wireless card.

Anyway, I'm going to go ahead and install Ubuntu on the hard drive, now my computer is back from the shop.

---

