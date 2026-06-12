---
title: "Cable Internet Connection"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by zinc00 on 2007-09-26
Hi,
I have a cable connection 2 the Internet, (works fine with XP) I'm using ubuntu live cd 7.04 and _[COLOR="DarkGreen"]NO ROUTER[/COLOR]_. I can't connect 2 the Internet,my ISP gave me this, but i get errors with no avail, pls help. 
(I was told 2 copy this 2 a file on my Desktop,named "cablestart".Help will be much appreciated!! 

_My PC Specs:_
CPU: 1.8 Dual Core2
NVIDIA 7600GT
RAM: 2GB
HD: 250GB

# This is a script used for connecting to Bezeq International through cable
# connection using the point to point tunnel protocol (PPTP) protocol.
# This script assumes the presence of a ppp daemon with MPPE support, and
# is written to correspond to pptp-linux 1.70, though it should work with
# any version above 1.5.
#
# Before using the script you should change the USERNAME variable to the
# user name you recieved from Bezeq International, and the IF variable to
# the name of the network interface card you will be using for the connection.
#
# Unless you've set the permissions in accordance, this script will only work
# when run as root.
#
# The script assumes that a PAP-secrets file already exists and that it
# contains an accurate password.
#
# This script runs a basic dialing procedure and does not support any error
# handling, therefor it's not recommended to make modifications any parts of
# the script other then the USERNAME and IF variables unless you know what you
# are doing.
#
# Bezeq International is not responsible for any demage that might result from
# running this script.
#
# Script by Shai Wyborski.

#!/bin/bash

#dialing properties
USERNAME=temp1
IF=eth0
ROUTE=`which route`

#reset the interface
/sbin/ifdown $IF
/sbin/ifup $IF

#inner routing
CABLEGW=`/sbin/route -n | grep ^0.0.0.0 | awk '{print$2}'`
PNS=`host tevelbi.bezeqint.net 192.168.101.101| awk '{print $4}' | grep .| head -1`
$ROUTE add -host $PNS gw $CABLEGW

#establish connection
/usr/sbin/pptp $PNS user $USERNAME mtu 1410 mru 1460 noauth usepeerdns &

echo Please standby...
sleep 10

#rerouting
NEWGW=`cat /var/log/messages | grep -i remote | tail -1 | awk '{print $9}'`
$ROUTE add default gw $NEWGW
OLDROUTE=`route -n | grep ^0.0.0.0 | awk '{print $2}' | tail -1`
$ROUTE del default gw $OLDROUTE
echo "nameserver 192.115.106.35" > /etc/resolv.conf
echo "nameserver 62.219.186.7" >> /etc/resolv.conf

---

### Post by mcduck on 2007-09-26
Could you tell us how are you trying to run that script, and what errors you get?

---

### Post by zinc00 on 2007-09-26
hi thx 4 responding..
**I was told to create 2 files on my Desktop, names "cablestart" & "cablestop":**
**_[COLOR="Blue"]1. In the file "cablestart" I pasted the following:[/COLOR]_**

# This is a script used for connecting to Bezeq International through cable
# connection using the point to point tunnel protocol (PPTP) protocol.
# This script assumes the presence of a ppp daemon with MPPE support, and
# is written to correspond to pptp-linux 1.70, though it should work with
# any version above 1.5.
#
# Before using the script you should change the USERNAME variable to the
# user name you recieved from Bezeq International, and the IF variable to
# the name of the network interface card you will be using for the connection.
#
# Unless you've set the permissions in accordance, this script will only work
# when run as root.
#
# The script assumes that a PAP-secrets file already exists and that it
# contains an accurate password.
#
# This script runs a basic dialing procedure and does not support any error
# handling, therefor it's not recommended to make modifications any parts of
# the script other then the USERNAME and IF variables unless you know what you
# are doing.
#
# Bezeq International is not responsible for any demage that might result from
# running this script.
#
# Script by Shai Wyborski.

#!/bin/bash

#dialing properties
USERNAME=temp1
IF=eth0
ROUTE=`which route`

#reset the interface
/sbin/ifdown $IF
/sbin/ifup $IF

#inner routing
CABLEGW=`/sbin/route -n | grep ^0.0.0.0 | awk '{print$2}'`
PNS=`host tevelbi.bezeqint.net 192.168.101.101| awk '{print $4}' | grep .| head -1`
$ROUTE add -host $PNS gw $CABLEGW

#establish connection
/usr/sbin/pptp $PNS user $USERNAME mtu 1410 mru 1460 noauth usepeerdns &

echo Please standby...
sleep 10

#rerouting
NEWGW=`cat /var/log/messages | grep -i remote | tail -1 | awk '{print $9}'`
$ROUTE add default gw $NEWGW
OLDROUTE=`route -n | grep ^0.0.0.0 | awk '{print $2}' | tail -1`
$ROUTE del default gw $OLDROUTE
echo "nameserver 192.115.106.35" > /etc/resolv.conf
echo "nameserver 62.219.186.7" >> /etc/resolv.conf
[B]
_[COLOR="Blue"]2. In the file "cablestopt" I pasted the following:[/COLOR]_[/B]

# This is a script used for closing a pptp connection.
#
# Before using the script you should change the IF variable to the name of
# the network interface card you will be using for the connection.
#
# Unless you've set the permissions in accordance, this script will only work
# when run as root.
#
# NOTICE that running this script will close all open PPTP connections, not
# just the one used for connecting to Bezeq International.
#
# Bezeq International is not responsible for any demage that might result from
# running this script.
#
# Script by Shai Wyborski.

#!/bin/bash

IF=eth0

killall pptp
/etc/init.d/network restart

ifdown $IF
ifup $IF

[B][U][COLOR="Blue"]3. The following commands and errors I copied off my terminal and saved into a text file..they all came out in one giant paragraph, I tried seperating the sentences to make it clear but im afraid it was getting worse,so I stopped.I hope someone who knows what they r doing can make some sence of the following:
These are the commands and responses I recieved following my ISP's support:[/COLOR][/U][/B]


ubuntu@ubuntu:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# cd /home/ubuntu/Desktop/
root@ubuntu:/home/ubuntu/Desktop# chmod a+x cable*
root@ubuntu:/home/ubuntu/Desktop# less cablestart

[1]+  Stopped                 less cablestart
root@ubuntu:/home/ubuntu/Desktop# less cablestart

[2]+  Stopped                 less cablestart
root@ubuntu:/home/ubuntu/Desktop# /usr/sbin
-bash: /usr/sbin: is a directory
root@ubuntu:/home/ubuntu/Desktop# mv cable* /usr/sbin
root@ubuntu:/home/ubuntu/Desktop# nano /etc/ppp/pap-secrets 
root@ubuntu:/home/ubuntu/Desktop# cablestart
: command not foundt: line 26: 
: command not foundt: line 28: 
: command not foundt: line 33: 
 not configurednterface eth0
.eth0ing unknown interface eth0
: command not foundt: line 37: 
: No such file or directory41: /sbin/route
: command not foundt: line 42: 
/usr/sbin/cablestart: line 44: /usr/sbin/pptp: No such file or directory
: command not foundt: line 44: 
: command not foundt: line 45: 
Please standby...
sleep: invalid time interval `10\r'
Try `sleep --help' for more information.
: command not foundt: line 48: 
: No such file or directory51: /sbin/route
: No such file or directory53: /sbin/route
: command not foundt: line 56: 
root@ubuntu:/home/ubuntu/Desktop# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:4D:05:7E:A5  
          inet addr:172.26.16.90  Bcast:255.255.255.255  Mask:255.255.224.0
          inet6 addr: fe80::2e0:4dff:fe05:7ea5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2256075 (2.1 MiB)  TX bytes:5938 (5.7 KiB)
          Interrupt:21 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

root@ubuntu:/home/ubuntu/Desktop# cablestart
: command not foundt: line 26: 
: command not foundt: line 28: 
: command not foundt: line 33: 
 not configurednterface eth0
.eth0ing unknown interface eth0
: command not foundt: line 37: 
: No such file or directory41: /sbin/route
: command not foundt: line 42: 
/usr/sbin/cablestart: line 44: /usr/sbin/pptp: No such file or directory
: command not foundt: line 44: 
: command not foundt: line 45: 
Please standby...
sleep: invalid time interval `10\r'
Try `sleep --help' for more information.
: command not foundt: line 48: 
: No such file or directory51: /sbin/route
: No such file or directory53: /sbin/route
: command not foundt: line 56: 
root@ubuntu:/home/ubuntu/Desktop# ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 7668
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:4d:05:7e:a5
Sending on   LPF/eth0/00:e0:4d:05:7e:a5
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 213.57.35.2 port 67
root@ubuntu:/home/ubuntu/Desktop# ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:e0:4d:05:7e:a5
Sending on   LPF/eth0/00:e0:4d:05:7e:a5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 10.230.192.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.230.192.1
bound to 172.26.16.90 -- renewal in 1355 seconds.
root@ubuntu:/home/ubuntu/Desktop# which ifdown
/sbin/ifdown
root@ubuntu:/home/ubuntu/Desktop# cablestart
: command not foundt: line 26: 
: command not foundt: line 28: 
: command not foundt: line 33: 
 not configurednterface eth0
.eth0ing unknown interface eth0
: command not foundt: line 37: 
: No such file or directory41: /sbin/route
: command not foundt: line 42: 
/usr/sbin/cablestart: line 44: /usr/sbin/pptp: No such file or directory
: command not foundt: line 44: 
: command not foundt: line 45: 
Please standby...
sleep: invalid time interval `10\r'
Try `sleep --help' for more information.
: command not foundt: line 48: 
: No such file or directory51: /sbin/route
: No such file or directory53: /sbin/route
: command not foundt: line 56: 
root@ubuntu:/home/ubuntu/Desktop# chgrp /usr/sbin/cablestart root
chgrp: invalid group `/usr/sbin/cablestart'
root@ubuntu:/home/ubuntu/Desktop# chgrp root  /usr/sbin/cablestart
root@ubuntu:/home/ubuntu/Desktop# cablestart
: command not foundt: line 26: 
: command not foundt: line 28: 
: command not foundt: line 33: 
 not configurednterface eth0
.eth0ing unknown interface eth0
: command not foundt: line 37: 
: No such file or directory41: /sbin/route
: command not foundt: line 42: 
/usr/sbin/cablestart: line 44: /usr/sbin/pptp: No such file or directory
: command not foundt: line 44: 
: command not foundt: line 45: 
Please standby...
sleep: invalid time interval `10\r'
Try `sleep --help' for more information.
: command not foundt: line 48: 
: No such file or directory51: /sbin/route
: No such file or directory53: /sbin/route
: command not foundt: line 56: 
root@ubuntu:/home/ubuntu/Desktop# pptp
The program 'pptp' is currently not installed.  You can install it by typing:
apt-get install pptp-linux
-bash: pptp: command not found
root@ubuntu:/home/ubuntu/Desktop# apt-get install pptp-linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  kernel-patch-mppe
The following NEW packages will be installed:
  pptp-linux
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/42.0kB of archives.
After unpacking 168kB of additional disk space will be used.
Selecting previously deselected package pptp-linux.
(Reading database ... 91545 files and directories currently installed.)
Unpacking pptp-linux (from .../pptp-linux_1.7.0-2ubuntu2_i386.deb) ...
Setting up pptp-linux (1.7.0-2ubuntu2) ...
root@ubuntu:/home/ubuntu/Desktop# chown root/usr/sbin/cablestart
chown: missing operand after `root/usr/sbin/cablestart'
Try `chown --help' for more information.
root@ubuntu:/home/ubuntu/Desktop# cablestart
: command not foundt: line 26: 
: command not foundt: line 28: 
: command not foundt: line 33: 
 not configurednterface eth0
.eth0ing unknown interface eth0
: command not foundt: line 37: 
: No such file or directory41: /sbin/route
: command not foundt: line 42: 
: command not foundt: line 44: 
: command not foundt: line 45: 
Please standby...
sleep: invalid time interval `10\r'
Try `sleep --help' for more information.
: command not foundt: line 48: 
': HOST NOT FOUND_address:pptp.c:377]: gethostbyname '212.179.61.78
: No such file or directory51: /sbin/route
: No such file or directory53: /sbin/route
: command not foundt: line 56: 
root@ubuntu:/home/ubuntu/Desktop# chown root /usr/sbin/cablestart
root@ubuntu:/home/ubuntu/Desktop# cablestart
: command not foundt: line 26: 
: command not foundt: line 28: 
: command not foundt: line 33: 
 not configurednterface eth0
.eth0ing unknown interface eth0
: command not foundt: line 37: 
: No such file or directory41: /sbin/route
: command not foundt: line 42: 
: command not foundt: line 44: 
: command not foundt: line 45: 
Please standby...
sleep: invalid time interval `10\r'
Try `sleep --help' for more information.
: command not foundt: line 48: 
': HOST NOT FOUND_address:pptp.c:377]: gethostbyname '212.179.61.78
: No such file or directory51: /sbin/route
: No such file or directory53: /sbin/route
: command not foundt: line 56: 
root@ubuntu:/home/ubuntu/Desktop# cablestart
: command not foundt: line 26: 
: command not foundt: line 28: 
: command not foundt: line 33: 
 not configurednterface eth0
.eth0ing unknown interface eth0
: command not foundt: line 37: 
: No such file or directory41: /sbin/route
: command not foundt: line 42: 
: command not foundt: line 44: 
: command not foundt: line 45: 
Please standby...
sleep: invalid time interval `10\r'
Try `sleep --help' for more information.
: command not foundt: line 48: 
': HOST NOT FOUND_address:pptp.c:377]: gethostbyname '212.179.61.78
: No such file or directory51: /sbin/route
: No such file or directory53: /sbin/route
: command not foundt: line 56: 
root@ubuntu:/home/ubuntu/Desktop# source cablestart
: command not found
: command not found
: command not found
 not configurednterface eth0
.eth0ing unknown interface eth0
: command not found
: No such file or directory
: command not found
': HOST NOT FOUND_address:pptp.c:377]: gethostbyname '212.179.61.78
: command not found
[3]   Exit 1                  /usr/sbin/pptp $PNS user $USERNAME mtu 1410 mru 1460 noauth usepeerdns
: command not found
Please standby...
sleep: invalid time interval `10\r'
Try `sleep --help' for more information.
: command not found
: No such file or directory
: No such file or directory
: command not found

---

### Post by BrendanM on 2007-09-26
First off, I'm almost astonished that a cable ISP even makes the effort to support Linux. Bravo to them. I would go through the lines that are coming back "command not found" and see if you can figure out what programs the script is looking for that you don't have. You could also try installing PPTP-Config which is a graphical frontend for PPTP, and then just get the ISP to give you the settings you need and use PPTP-Config instead of their own script. Good luck to you.

---

### Post by zinc00 on 2007-09-26
"You could also try installing PPTP-Config which is a graphical frontend for PPTP, and then just get the ISP to give you the settings you need and use PPTP-Config instead of their own script."
How and where do I get/install "PPTP-Config"?
thx m8

---

### Post by zinc00 on 2007-09-29
Theres still no success in connecting 2 the Internet through a cable-modem ISP connection...anyone??...through me a bone....plz

---

### Post by zinc00 on 2007-10-16
Help connecting 2 the Internet through a cable-modem ISP connection...anyone?? :confused:  ](*,):frown::roll:

---

