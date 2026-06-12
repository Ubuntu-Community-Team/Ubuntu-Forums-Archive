---
title: "network settings"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by OAP on 2007-12-26
installed 7.04 and tried to connect via dial-up modem, failed [surprise!],now have ADSL modem but no 'wired connection'  [or wireless] choice in network settings , how do i get them back? am complete beginner.

---

### Post by spiderbatdad on 2007-12-26
if your system was installed before you had a working connection, i suppose it is possible network tool were not installed. You will probably need the live cd, then navigate to synaptic package manger and look for the network tools shown in the screenshot below. You will also need to make sure the cd is a software source under system-->administration-->software sources. It probably is.Then REBOOT. If this is a usb adsl modem, another post claims in Gutsy a connection wizard starts after 2 attempt, idk about fiesty. There is also reference to several guides for seting up a usb adsl modem here:[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)

---

### Post by OAP on 2007-12-27
thanks for reply, tried suggestion with live cd no joy, according to synaptic package manager all the relevant network packages are installed,i am trying to connect via ethernet not usb.

---

### Post by mellowd on 2007-12-27
If you are trying to connect via ethernet it should automatically pick up an address. can you do this:

open a terminal and type:

```
ifconfig
```

paste the results here

---

### Post by OAP on 2007-12-27
typed as requested no result

---

### Post by mellowd on 2007-12-27
nothing at all? just a blank screen?

---

### Post by OAP on 2007-12-27
result of inconfig (2nd attempt):-
lo            Link  encap:local  Loopback
               inet  addr:127.0.0.1  Mask:255.0.0.0
               inet6  addr:  ::1/128  Scope:Host
               UP LOOPBACK RUNNING  MTU:16436  Metric :1
               RX packets:2  errors:0 dropped:0 overruns:0  frame: 0
               TX packets:2  errors:0 dropped;0 overruns:0 carrier:0
               collisions:0 txqueuelen: 0
               RX  bytes:100 (100.0 b)    TX bytes:100  (100.0 b)

---

### Post by spiderbatdad on 2007-12-27
try this to make sure  the interfaces are up:```
sudo eth0 up && sudo eth1 up
```

then run ```
sudo dhclient eth0 && sudo dhclient eth1
``` to request an ip

---

### Post by OAP on 2007-12-27
result of:- sudo eth0 up ...etc  command not found
result of:- sudo  dhclient ...etc  for info visit [www.isc.org/sw/dhcp/](www.isc.org/sw/dhcp/)
                                                   SIOCSIFADDR:no such device
                                                   eth0: error (repeated)
                                                   Bind socket to interface :no such device

i have'n't had this much fiddling since i fitted a Vincent 1000 engine in a Norton featherbed frame!

---

### Post by spiderbatdad on 2007-12-27
thats a 0 (zero) not a capital o

i have'n't had this much fiddling since i fitted a Vincent 1000 engine in a Norton featherbed frame.":lolflag:

---

### Post by Linuxratty on 2007-12-27
Is this on a Dell machine?

---

### Post by spiderbatdad on 2007-12-27
```
lspci
```  please.

---

### Post by OAP on 2007-12-27
i did use zero, the 2nd last line reads, eth0: error while getting interface flags:no such device(repeated).

---

### Post by OAP on 2007-12-27
yes, it is a dell Inspiron 530 E2140 pent dual core proc.

---

### Post by spiderbatdad on 2007-12-27
could you post the output of ```
sudo lshw -C Network
```

also your reply did not contain ant information about eth1, which is what i thought you were try to configure.

---

### Post by spiderbatdad on 2007-12-27
for example:
```


-laptop:~$ sudo lshw -C Network
  *-network:0             
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:d0:59:c8:5b:fa
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=airo ip=192.168.15.103 latency=64 maxlatency=4 mingnt=4 module=airo multicast=yes wireless=IEEE 802.11-DS
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:02:3f:09
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd

```

---

### Post by OAP on 2007-12-28
i did use a zero,the full result of  sudo dhclient ......etc  is  Internet System Consortium DHCP Client V3.0.4 copyrite 2004-6 ISC for info visit.....etc
2nd last line is... eth0:error while getting interface flags:no such device

---

### Post by mellowd on 2007-12-28
Seems to me your network just isnt getting recognised. What network card is it?

---

### Post by Biggy on 2007-12-28
download UbuDSL and install it 

download [Here]("http://linux.softpedia.com/progDownload/UbuDSL-Download-30037.html")

---

### Post by OAP on 2007-12-28
sorry i did'n't see your last reply until now ,the result of, sudo 1shw _C network, was command not found.

---

### Post by spiderbatdad on 2007-12-28
sorry, but if you get command not found, especially where the command is illustrated in the above post, then you should check for typos, ```
sudo lshw -C Network
```

that is not a one. It is a lower case L.  also -C  is a capital c, and the n in network is capitalized...Network. It all means something like:
list hardware of the class (or category)network.

---

### Post by OAP on 2007-12-28
result of sudo lshw -C Network :-*-network UNCLAIMED
description: Ethernet controller
product: intel corp
vendor: intel corp
physical id:19
bus info:pci@00:19.0
version:02
width:32 bits
clock:33Mhz
capabilities:bus_master cap_list
config:latency=0

---

### Post by spiderbatdad on 2007-12-28
try these commands one at a time please.



Code:

sudo ifup eth0

Code:

sudo ifdown eth0


Code:

sudo dhclient eth0


Code:

sudo /etc/init.d/networking start

---

### Post by spiderbatdad on 2007-12-28
where it says bus info@pci 00:19.0   i dont think looks quite right. check ```
lspci
```

just to be sure. and where it shows your card, in bold below, you should see something like  02:blah  or 04:blah   I'm not 100% sure but I think what you have is not a recognized driver...but one may be available.  This is the section of my "lspci" that lists network interfaces: If yours starts with 00:  then you need a driver.

```
02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b
**02:08.0** Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

```

---

### Post by OAP on 2007-12-28
entered lspci all the devices listed started with 00:  including 00:19.0 ethernet controller: intel corp. unknown device, the only one with a no. is 02:01.0 Communication controller:Conexant HSF 56k Data/Fax Modem, the dial-up that did not work.

---

