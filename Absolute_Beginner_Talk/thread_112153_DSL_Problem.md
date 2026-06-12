---
title: "DSL Problem"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by ric..hard on 2006-01-03
Hi All,

Good Day.

Newbie Question.

I have a DSL working in windows. Its using DHCP or something but there
was an error getting IP from the network. The customer support had to
give me the ip address so i can connect from inside windows.

Now I have succesfully setup the latest Kubuntu ( Breezy ) in my
laptop. I have set the same IP address I am using in windows for the
DSL connection. But I still have no connection.

Any help is appreciated.

Thanks

Some Infos....

```
Provider is Digitel/Mozcomm in Philippines
```

```
sandman@earlgrey:~$cat  /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
       script grep
       map eth0

iface eth1 inet

iface eth0 inet static
address 10.0.0.56
netmask 255.0.0.0

auto eth0
sandman@earlgrey:~$
sandman@earlgrey:~$
sandman@earlgrey:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:12:3F:E8:0E:6A
         inet6 addr: fe80::212:3fff:fee8:e6a/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b)  TX bytes:324 (324.0 b)
         Interrupt:18

sandman@earlgrey:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
sandman@earlgrey:~$
sandman@earlgrey:~$
sandman@earlgrey:~$ cat /etc/resolv.conf
nameserver 202.138.128.50
nameserver 202.138.128.2
sandman@earlgrey:~$
sandman@earlgrey:~$
sandman@earlgrey:~$
sandman@earlgrey:~$ sudo mii-tool eth0
Password:
eth0: negotiated 100baseTx-FD flow-control, link ok
sandman@earlgrey:~$
sandman@earlgrey:~$
sandman@earlgrey:~$ lspci | grep Eth
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0
100Base-TX (rev 02)
sandman@earlgrey:~$
sandman@earlgrey:~$
sandman@earlgrey:~$
sandman@earlgrey:~$ lsmod | grep mii
mii                     5248  1 b44
sandman@earlgrey:~$
```

---

### Post by ric..hard on 2006-01-03
Hi All,

Please visit other thread for more comments and help .

[http://www.ubuntuforums.org/showthread.php?t=112012](http://www.ubuntuforums.org/showthread.php?t=112012)

I was not aware that emails to the mailing list will find its way here.

Thanks

richard

---

### Post by noeluylee on 2006-01-03
Make sure you have setup your dns on networking setings. :-)

---

### Post by thekiller on 2006-01-03
if its a DHCP connection then just do

```

sudo dhclient3 eth0

```

---

### Post by proventech on 2006-01-03
some ISPs require you to register you MAC address with them.  check with them to see if that is the case.  If it is, you may have to clone you MAC address in ubuntu (i do not know how but maybe someone else does).
even if this in not the case, sometimes the MAC address your computer has gets stuck in their circuits and does not get released properly.  if you plug in you other computer and run ipconfig/release then quickly unplug the ethernet cable and plug it into you linux maching, it might work for you.

---

