---
title: "Wifi Help needed!"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-06-02
Ok I am starting over with a fresh install of Dapper 6.06. I have a zd121 usb wifi. The device was recognized and the driver loaded automatically.

**lsmod:** shows zd1211 loaded
**iwconfig:** shows that is has been associated with my router and ESSID and has a signal
**ifup wlan0:** states that is is already configured
**ping 192.168.1.1:** [COLOR="Red"]network unreachable[/COLOR] 

Any ideas of what is going on or what to try next?
Thanks

---

### Post by murph2481 on 2006-06-02
Try 'sudo dhclient' to release and renew the ip address

---

### Post by bluefrog on 2006-06-02
have a look at system > adminstration > networking

James

---

### Post by rubrboots on 2006-06-02
Ok 

I tried ```
sudo dhclient
```
end result was:
no DHCPOFFERS recieved
no working leases in persistant database - sleeping

And I have already set it up in the NETWORKING GUI. It sees my network essid as well as my neighbours. I have it set for DHCP, with no sercurity.

---

### Post by murph2481 on 2006-06-02
so looks like your router isn't releasing an IP address to your computer.  if you type

ifconfig

What do you see?

---

### Post by rubrboots on 2006-06-02
Since I have no internet on that machine Ive had transfer it over via usbdisk. Sorry it look pretty messy

**ifconfig:**

UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000
          
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          
Interrupt:185 Base address:0xdc00

lo        
Link encap:Local Loopback
          
inet addr:127.0.0.1  Mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host
          
UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0
          
RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

wlan0     
Link encap:Ethernet  HWaddr 00:02:72:4F:88:FE
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000
          
RX bytes:3810 (3.7 KiB)  TX bytes:0 (0.0 b)


**iwconfig:**

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     802.11b/g NIC  ESSID:"McCarron"
          
Mode:Managed  Frequency=2.462 GHz  
Access Point: 00:0F:66:8A:BD:0D
          
Bit Rate:11 Mb/s
          
Retry:off   RTS thr=2432 B   Fragment thr:off
          
Power Management:off
          
Link Quality=76/92  Signal level=34/154  Noise level=161/154

Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          
Tx excessive retries:524  Invalid misc:0   Missed beacon:0



sit0      no wireless extensions.

---

### Post by bt224 on 2006-06-02
Before you run down too many rabbit trails, thought I would mention that a lot of wired users are having this same issue. Dapper doesn't seem to want to keep a DHCP lease for more than a few seconds. I can unplug the cable, replug, and get internet for about 30 seconds. Maybe see if you unplug the router/access point from the network, and when you replug if you get anything. If you get internet. then it might be somoething other than your wi-fi card. Just a thought.

---

### Post by rubrboots on 2006-06-02
Tried that, but it made no difference. That gave me the idea to try a static ip address. With a static ip it will actually ping now, but now states that destination host is unreachable, instead of network unreachable.](*,)

---

