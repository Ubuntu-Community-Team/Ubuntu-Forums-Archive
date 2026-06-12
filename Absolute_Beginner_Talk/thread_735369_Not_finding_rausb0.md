---
title: "Not finding rausb0"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by nick937 on 2008-03-25
usually when I plug in my hawking hwug1 USB wirless adapter, it automatically comes up.
but now when i try and do ifconfig rausb0 up
```
: error fetching interface information: Device not found

```
but, I can still use it if I have a virtual machine is running. So I know that the adapter works, it just wont recognise it as a wirelss device...

---

### Post by nick937 on 2008-03-25
anyone..?

---

### Post by jan quark on 2008-03-25
when you have the adapter plugged in try this to restart the network
```

sudo /etc/init.d/networking restart
```

---

### Post by nick937 on 2008-03-25
still nothing
```

nick@t00r:~$ sudo /etc/init.d/networking restart
[sudo] password for nick: 
 * Reconfiguring network interfaces...                                   [ OK ] 
nick@t00r:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:107088 (104.5 KB)

br0:avahi Link encap:Ethernet  HWaddr 00:xx:xx:xxxx
          inet addr:1xx.xx4.x.x9  Bcast:1xx.2xx.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx 
          UP BROADCAST PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9657 (9.4 KB)  TX bytes:9657 (9.4 KB)

tap0      Link encap:Ethernet  HWaddr 00:ff:f3:cd:1e:f4  
          inet addr:192.168.0.94  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:622 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:479244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:351539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:592910856 (565.4 MB)  TX bytes:34262315 (32.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-xx-xx-xx-xx-xx-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nick@t00r:~$ 

```
Wlan0 is my internal wireless card

---

### Post by nick937 on 2008-03-26
I also tried the 'ifconfig rausb0 up' command and it still didnt not work. It was also not listed in iwconfig.. Even when I start up my computer with the USB adapter plugged in, it still does not show up on here

---

### Post by Bachstelze on 2008-03-26
Try with wlan0 instead of rausb0.

---

### Post by nick937 on 2008-03-26
wlan0 is my internal wireless card

---

### Post by Bachstelze on 2008-03-26
There is no rausb0, so if you have a wireless adapter other than wlan0, it is either not working, not connected, or it's driver is not installed.

---

### Post by nick937 on 2008-03-26
ok so, it is plugged in. and it shows up in virtualbox as a wireless adapter.
so i dont see what is wrong. It worked a few weeks ago perfectly. and now I can use it, but only when virtualbox is on..but I cant use it on my host system. Since it works on Vbox Through my host system, doesnt this mean the driver is installed still?
So
Not working - nope it works.
Driver installed-it works through the host system to virtual machine, so I think this means yes.
plugged in-yes

---

### Post by nick937 on 2008-03-27
I just tried re-installing the drivers for it, and it said that they were already included with my kernel.

---

### Post by ghost_ryder35 on 2008-03-27
are you running a virtual machine at the same time?  the virtual machine may take ownership of the USB device and therefor the host does not see it or use it

---

### Post by nick937 on 2008-03-27
nope... it does not work at all when a virtual machine is not running

---

### Post by nick937 on 2008-03-28
so basically no one knows why this is happening?

---

### Post by nick937 on 2008-04-03
any other ideas?
```

lsusb
Bus 007 Device 005: ID 148f:2573 Ralink Technology, Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1130:6606 Tenx Technology, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

```
it shows up under lsusb as Ralink...
I just don't understand why its not working

---

