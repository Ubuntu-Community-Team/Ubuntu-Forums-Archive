---
title: "Breezy B. Weird Wireless Problem"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by Sniperwolf on 2005-09-27
Im very new to Linux, but ill admit a month ago i downloaded Ubuntu Live CD to experience it, and i loved it. Finally after alot of different linux research i thought the best first linux i experienced would be the right one for me. 
Ive installed it, and thats all good, but wireless is my problem. Im using Breezy Badger so i understand if its a bug, or something.
I thought i set up the network right, but when i try to set it up, and unplug from wired internet, firefox wont load the page. It says it cant find it in that pop up box. The odd thing is in the icon in the top corner, it says i have a strong connection. What am i dooing wrong, or what can i post to help you help me?

---

### Post by mlomker on 2005-09-27
These would be a good place to start:

```

iwconfig
ifconfig
cat /etc/network/interfaces

```

---

### Post by Sniperwolf on 2005-09-28
IWCONFIG> lo        no wireless extensions.
eth0      no wireless extensions.
ath0      IEEE 802.11g  ESSID:"default"
Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:74:FD:8E
Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
Retry:off   RTS thr:off   Fragment thr:off
Power Management:off
Link Quality=49/94  Signal level=-46 dBm  Noise level=-95 dBm
Rx invalid nwid:356  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sit0      no wireless extensions.
IFCONFIG > ath0      Link encap:Ethernet  HWaddr 00:13:46:0E:7A:65
inet6 addr: fe80::213:46ff:fe0e:7a65/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:1345 errors:70988 dropped:0 overruns:0 frame:70988
TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:200
RX bytes:455258 (444.5 KiB)  TX bytes:12348 (12.0 KiB)
Interrupt:11 Memory:dcac0000-dcad0000
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:A6:AE:CF
inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
inet6 addr: fe80::20b:cdff:fea6:aecf/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:85703 errors:0 dropped:0 overruns:0 frame:0
TX packets:44886 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:126663262 (120.7 MiB)  TX bytes:3250277 (3.0 MiB)
Interrupt:10 Base address:0xe000
lo        Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:13663 errors:0 dropped:0 overruns:0 frame:0
TX packets:13663 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1011428 (987.7 KiB)  TX bytes:1011428 (987.7 KiB)
cat /etc/network/interfaces > # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0
# The primary network interface
iface eth0 inet dhcp
iface ath0 inet dhcp
wireless-essid default
wireless-key s: (encryption key here, and yes, its correct)
auto ath0
iface dsl-provider inet ppp
provider dsl-provider
auto eth0

---

### Post by Mustard on 2005-09-28
Using the [noparse]```
 text 
```[/noparse] format will get rid of those smilies.

---

### Post by mlomker on 2005-09-28
From your post it looked like you were associated fine (wep keys are fine) but the interface did not have an IP address.

Try unplugging the eth0 and then in a terminal prompt **sudo dhclient ath0**.

---

### Post by Sniperwolf on 2005-09-28
Thanks for the support, but actually its working now. What i did was use the add applications list, and got wifi radar. I guess that got the IP address for me. At least i know these forums are a friendly and reliable place when i have a problem that i cant solve.

---

