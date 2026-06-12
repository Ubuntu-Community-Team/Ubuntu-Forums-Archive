---
title: "Dapper Drake..."
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by nuubuntu on 2006-02-23
I installed the Dapper Drake Flight CD 4 because I thought that the OS may notice my wireless card. Under that hunch, it actually showed up. Now the problem is that the device radio isn't turning on. For example, the wireless light on the laptop does not show up. is there a way to turn it on. I saw a post about turning it on when you have ndiswrapper installed, but I have no idea how to activate it when it is not configured with ndiswrapper. Any help would be appreciated: The following shows the what is going on, i guess....

```
oem@ubuntuxu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"JuBuBUbu"  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          Tx-Power=off
          RTS thr:off   Fragment thr:off
          Encryption key:3839-4230-3238-4541-3535-0000-00   Security mode:open

eth1      no wireless extensions.

sit0      no wireless extensions.

```

Again, all the help would be appreciated. I am a super new user to Linux, and I would like to learn it as much as possible. Thanks.

---

### Post by Brunellus on 2006-02-23
sudo ifup eth0

---

### Post by loupy on 2006-02-23
Although Dapper does indeed recognize BCM43xx cards - it is not allowed to include the firmware required to run the card.  You need to use fwcutter against the windows driver xxxx.sys to create the xxxx.fw files to put into /lib/firmware so that it will work.

---

### Post by nuubuntu on 2006-02-23
**Brunellus**, I have tried to type that in and I got the following response:

```
oem@ubuntuxu:~$ sudo ifup eth0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth0/00:90:96:8f:25:2a
Sending on   LPF/eth0/00:90:96:8f:25:2a
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

**loupy**, I am sorry, but I have no idea where to start with the instructions that you listed on there. 

loupy, Brunellus, thanks you for your time and help.

---

### Post by loupy on 2006-02-24
**nuubuntu** IM me and I can walk you through it.

---

### Post by nuubuntu on 2006-03-02
I am sorry everyone, I have been away from any computers for a while. I will traveling again this thursday again. Be back Sunday, March 5th. Sorry. I have been way too busy to look at the Dapper machine. Thanks to everyone.

---

