---
title: "persistent wifi probs"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by scholzilla on 2007-11-03
Hi,

I've had other users here try to solve this one, but to no avail and thought I'd give it another shot. My wifi drops connections all the time, regardless of AP. I'm using wicd because network manager wouldn't even see wifi. I can usually only reconnect after rebooting my computer. 
How do I know if the problem is hardware or software based?

Below is 1) the output I get when I try to disable and reenable my wifi and 2) general specs. Any help would be deeply appreciated.  I wonder if it has something to do with the "unknown hardware address type" line? All worked fine months ago.

---------
matt@matt-laptop:~$ sudo ifdown -v wlan0
Password:
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5371
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:c0:a8:d8:96:a1
Sending on   LPF/wlan0/00:c0:a8:d8:96:a1
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
ifconfig wlan0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant
matt@matt-laptop:~$ sudo ifup -v wlan0
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "Actually1".
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -pf /var/run/dhclient.wlan0.pid -lf /var/lib/dhcp3/dhclient.wlan0.leases wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:c0:a8:d8:96:a1
Sending on   LPF/wlan0/00:c0:a8:d8:96:a1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant
---------------
Here are my specs:


matt@matt-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:D3:D8:D5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9575 (9.3 KiB)  TX bytes:9575 (9.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:D8:96:A1  
          inet6 addr: fe80::2c0:a8ff:fed8:96a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12238765 (11.6 MiB)  TX bytes:1396980 (1.3 MiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:C0:A8:D8:96:A1  
          inet addr:169.254.10.22  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-D8-96-A1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.437 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"You_No_Use"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

---

### Post by donkeykidd218 on 2007-11-03
I had the exact same problems that you had while I was using older Ubuntu distros, I either couldn't connect to my Wireless or it would suddenly disconnect, but 7.10 seems to have fixed that for me. Have you tried using the newest distro? Just a suggestion.

---

### Post by scholzilla on 2007-11-03
thanks--i haven't been updating my kernel b/c of a bug that kills my sound (long story). I may have to wait for gutsy's release.

---

