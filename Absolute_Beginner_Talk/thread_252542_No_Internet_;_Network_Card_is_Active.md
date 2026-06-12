---
title: "No Internet ; Network Card is Active"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by mango.muncher on 2006-09-06
Hello, I'm new 2 Linux. I have Ubuntu Dapper Drake on a Dell Dimesnion 3000, Dual Boot.

The load was a mission , but thats another story. The drake is running now but I can't access the internet.
I have browsed for hours and have attempted to correct fault but no luck.

I have a DSL modem (D-Link 502t), my network card shows as active and I can ping the modem at 10.1.1.1

Other fault isolation to date:
Installed another PCI network card in case of driver problems. Changed cables. 
Checked DSL was set up OK (XP can use either card to access internet).
Ran pppoeconf (I had a text file but XP cant read it) and got 'Scanned 2 interfaces but Access controller did not respond.'
Ran ipconfig and cant remember ........ I boot up Ubuntu again and save text dump as another format.
Be back soon.......

---

### Post by mango.muncher on 2006-09-06
Hmmm XP can't open that format either. So no text dumps are forth coming.

---

### Post by cwaldbieser on 2006-09-07
> **mango.muncher said:**
> Hmmm XP can't open that format either. So no text dumps are forth coming.

Can you copy the dump to a floppy or a thumb-drive?

```

$ ifconfig > interface.txt
$ route > routing-table.txt

```
Puts the data in files, then just copy the files to the removable storage.  You should be able to open them in notepad in Win XP.

---

### Post by hollym on 2006-09-07
I seem to be having the exact same problem. The output from those files from my computer is 

The output $route
$route 
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref
*(no information - is this the problem?)*

$ifconfig
Link encap:Ethernet HWaddr 00:0C:6E:11:1B:3B
inet6 addr: fe80::20c:6eff:fe11:1b3b/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1633 errors:0 dropped:0 overruns:0 frame:0
TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:97980 (95.6 KiB) TX bytes:4230 (4.1 KiB)
Interrupt:201 Base address:0x9800lo

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:135 errors:0 dropped:0 overruns:0 frame:0
TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:10196 (9.9 KiB) TX bytes:10196 (9.9 KiB)

So, apparently I dont have a gateway or something ... suggestions?

---

### Post by mango.muncher on 2006-09-07
Hi cwaldbieser, here is ifconfig

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::213:20ff:fe8f:3490/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1598 (1.5 KiB)  TX bytes:1818 (1.7 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)


And Routing........

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.0.0.0       U     0      0        0 eth0
default         mygateway1.ar7  0.0.0.0         UG    0      0        0 eth0

Thanks for assistance:-D

---

### Post by mango.muncher on 2006-09-07
Am I correct to suspect that interface address, it looks wrong.
If any one knows a fix.....Im going searching.

---

### Post by mango.muncher on 2006-09-07
FYI I found some good info at [http://linux-ip.net/html/basic-changing.html](http://linux-ip.net/html/basic-changing.html)
I will let forum know how it goes....but will be away from c'puter for 4 days. Maybe the little people will fix it for me :)

---

### Post by mango.muncher on 2006-09-11
Update for veiwers with similar problem: 
Good info found at [http://www.ubuntuforums.org/showthread.php?t=250149](http://www.ubuntuforums.org/showthread.php?t=250149)
As discussed in above thead the Dlink 502 IP address was being read as a server IP. I am using 6.06 desktop. I went to System/Admim/Networking/dns and deleted the existing IP which was 10.1.1.1 and added my ISP ip address. 
I got the ISP address by entering my D Link router address 10.1.1.1 (login/pw is normally admin + admin) into firefox and then went to Status tab, look for DNS Server address.

This new IP address hooked me up to internet.

I also commented out the /etc/resolv.conf as suggested as on reboot the correct IP address was getting replaced by the router address.

Edit: All good now.

---

