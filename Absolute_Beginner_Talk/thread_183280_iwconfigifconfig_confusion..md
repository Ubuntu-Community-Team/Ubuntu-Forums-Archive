---
title: "iwconfig/ifconfig confusion."
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-05-27
This is the output of ifconfig:

ra0       Link encap:**Ethernet**  HWaddr 00:10:60:27:30:1C
          inet6 addr: fe80::210:60ff:fe27:301c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
          TX packets:66921 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:3479892 (3.3 MiB)
          Interrupt:11 Base address:0xc000

And this is the output of iwconfig

ra0       RT2500 **Wireless**  ESSID:"WANADOO-3EB4"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm
          RTS thr: off   Fragment thr: off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-208 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

They are both about the same device (ra0) but one of them says ETHERNET and one of them says WIRELESS. How can I change them both to WIRELESS. Is this normal?! ](*,)

---

### Post by skippy81 on 2006-05-27
Its looks fine to me.  The key question is "is it working?" :D

---

### Post by tartarian on 2006-05-27
And the answer to that very probing question is NO! cry.

It looks ok? But its the same wireless device, but one says Ethernet:
a0 Link encap:Ethernet HWaddr 00:10:60:27:30:1C
and one says wireless:
ra0 RT2500 Wireless ESSID:"WANADOO-3EB4"

surely thats not right. Or am i being stupid?! lol

---

### Post by Stewart on 2006-05-27
With my wireless ipconfig says it is also Ethernet, but it works fine, so I dont think thats your problem.

In your output from iwconfig it looks like the power is set to 0 (Tx-Power:0 dBm) and your Link Quality=0/100.

Try "iwconfig ra0 txpower auto"  or "iwconfig ra0 txpower on" in a terminal and see if that helps.

Just a guess, but worth a shot.

Try "man iwconfig" in a terminal for more info on other settings.

Stewart

---

