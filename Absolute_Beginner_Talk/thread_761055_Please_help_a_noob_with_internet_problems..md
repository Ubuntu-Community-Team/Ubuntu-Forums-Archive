---
title: "Please help a noob with internet problems."
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by id1337x on 2008-04-20
I've tried getting help before on my problems but I guess I didn't have enough information. Anyways I have a HP pavillion a633f PC with Ubuntu 7.10 and I have a RTL 8111/8168 Express Ethernet Gigabit Controller.

lshw -C network:

```
*-generic
  description: Ethernet interface
  product: Illegal Vendor ID
  vendor: Illegal Vendor ID
  physical id: 0
  businfo: pci@0000:0Z:00.0
  logical name: eth0
  version: ff
  serial: 00:le:8c:35:9c:76
  width: 32 bits
  capabilities: bus_master vga_palette cap_list ethernet physical
  configuration: broadcast=yes driver=8169 driverversion=2.2LK latency=255 maxlatency=255 minint=255 module=r8169 multicast=yes
```

route

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
```

ifconfig

```
eth0         Link encap: Ethernet HWaddr 00:1E:8C:35:89:9C:7B
             UP BROADCAST RUNNING MULTICAST MTU:1500 Metric: 1
             RX packets: 0 errors: 0 dropped: 4294967289 overruns: 0 frame: 0
             TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
             collisions: 0 txqueuelen: 1000
             RX bytes: 0 (0.0 b)  TX bytes: 0 (0.0 b)
             Interrupt: 17 Base Address: 0x2000

lo           Link encap: Local Loopback
             inet addr: 127.0.0.1 Mask: 255.0.0.0
             UP LOOPBACK RUNNING MTU: 16436 Metric: 1
             RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
             TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
             collisions: 0 txqueuelen: 0
             RX bytes: 0 (0.0 b) TX bytes 0 (0.0 b)
```

---

### Post by spiderbatdad on 2008-04-20
This is from a bug filed on lauchpad for a similar card. It may help you...[https://answers.launchpad.net/ubuntu/+question/18140](https://answers.launchpad.net/ubuntu/+question/18140)
```
Dear Mar cobra,

Thanks for your reply,
I have discussed this problem with one of my friend and he suggested me to do this
su root
password
mii-tool -F 10baseT-HD
sudo /etc/init.d/networking restart
mii-tool -R

After these number of commands my net starts working and i was delightful.
But he told me do this every time I boot in to ubuntu.
is there any permanent solution by which it can work with out entering any more commands after i boot because this system will be used by my parents who are not familiar with this OS.
looking forward for your reply soon.

Thank You
Best  marcobra said on 2007-11-21:

Try to open your /etc/rc.local

sudo gedit /etc/rc.local

and add your desired row into that file:

mii-tool -F 10baseT-HD
sudo /etc/init.d/networking restart
mii-tool -R

Please be sure, don't touch, at the end of file, the "exit 0" instruction

Hope this Help
 Ramakrishna said on 2007-11-21


```

---

### Post by id1337x on 2008-04-20
Ya when I do **mii-tool -F 10baseT-HD** it returns:

```
SIOCGMIIPHY on 'eth0' failed: Operation not supported
no MII interfaces found
```

---

### Post by id1337x on 2008-04-22
Should I post this somewhere else or something?

---

### Post by jackflap on 2008-04-22
What does it say when you do a 'sudo dhclient eth0'?

Do another ifconfig after it's finished as well please. What is the network card plugged into? What kind of router?

---

