---
title: "wlassistant strange startup"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by rickdog on 2007-03-26
Okay, I can get Wireless Assistant to work, not automatically, but using sudo it works, however I get this:

[COLOR="RoyalBlue"]rick@rick-laptop:~$ sudo wlassistant
Password:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

wifi0     no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): ath0
Permissions checked.
ifconfig_status: /sbin/ifconfig ath0
scan: /sbin/iwlist ath0 scan
Networks found: 1
Checking for active connection.
Trying to get gateway address...
...from 'route'
No default gateway.
ACTION: CONNECT.
kill_dhcp: /sbin/dhclient -r ath0
==>stderr: Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:90:96:7f:03:81
Sending on   LPF/ath0/00:90:96:7f:03:81
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
ifup: /sbin/ifconfig ath0 up
iwconfig_set: /sbin/iwconfig ath0 mode managed channel 6 key open ************************** essid HOME
iwconfig_ap: /sbin/iwconfig ath0 ap 00:0D:88:EB:96:7E
ifconfig_dhcp: /sbin/dhclient -q ath0
==>stderr: There is already a pid file /var/run/dhclient.pid with pid 134993416
Trying to get gateway address...
...from 'route'
Gateway address: 192.168.1.1
Application options saved.
Kernel socket closed.
rick@rick-laptop:~$ 
[/COLOR]

First of all, I'm running this in ubuntu instead kubuntu, does this matter?

And I would like to streamline the above process somehow.

:guitar:

---

