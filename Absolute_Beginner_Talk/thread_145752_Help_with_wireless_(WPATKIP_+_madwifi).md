---
title: "Help with wireless (WPATKIP + madwifi)"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by 18x on 2006-03-16
I'm using madwifi drivers, wpasupplicant, and dhcp. Drivers work. I can associate fine, authenticate fine, but when it comes to pulling an IP I'm having some serious issues. I have wpasupplicant running before networking in startup (as per the tutorials I've found). I've included some output below that may give you an idea of what's happening.

iwconfig:
ath0      IEEE 802.11g  ESSID:"18x"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:02:72:4D:4D:A3
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/94  Signal level=-38 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:
ath0      Link encap:Ethernet  HWaddr 00:04:E2:FA:B5:BE
          inet6 addr: fe80::204:e2ff:fefa:b5be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:16910 dropped:0 overruns:0 frame:16910
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:15910 (15.5 KiB)  TX bytes:6954 (6.7 KiB)
          Interrupt:11 Memory:c8aa0000-c8ab0000

wpa_cli status:
Selected interface 'ath0'
bssid=00:02:72:4d:4d:a3
ssid=18x
pairwise_cipher=TKIP
group_cipher=TKIP
key_mgmt=WPA-PSK
wpa_state=COMPLETED
Supplicant PAE state=AUTHENTICATED
suppPortStatus=Authorized
EAP state=SUCCESS


The problem is when running dhclient. I've been typing 'sudo dhclient ath0' but it's just been stuck on DHCP DISCOVER. Here is the contents of my /etc/network/interfaces file:
auto lo
iface lo inet loopback
mapping hotplug
        script grep
        map eth0
iface eth0 inet dhcp
iface ath0 inet dhcp
auto ath0
auto eth0

I really hope that I'm not missing something extremely simple...

---

