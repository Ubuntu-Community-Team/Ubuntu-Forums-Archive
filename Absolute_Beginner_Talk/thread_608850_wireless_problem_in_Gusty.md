---
title: "wireless problem in Gusty"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by Mikebar on 2007-11-10
Hi All,
I had my Linksys WUSB11 wireless working in Feisty with Wifi Radar but since upgrading to gusty i can not get it to work.

 I have followed the following post [http://ubuntuforums.org/showthread.php?t=602584]("http://ubuntuforums.org/showthread.php?t=602584") but when I add my WEP and type
[HTML]sudo dhclient wlan0[/HTML]
I get the following error
[HTML]mike@mike-desktop:~$ sudo dhclient wlan0
[sudo] password for mike:
There is already a pid file /var/run/dhclient.pid with pid 6741
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:17:97:84:bb
Sending on   LPF/wlan0/00:12:17:97:84:bb
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
mike@mike-desktop:~$ 
[/HTML]

I have used Ndiswrapper to install the windoze drivers and all is installed fine.

Can anyone please HELP me PLEASE :confused:

---

### Post by skanchi on 2007-11-11
Before you request for an IP address, check the wireless link is up. type dmesg, and check for link up message. 
Other things to check are the association to the AP. Issue the command "iwconfig wlan0"

---

### Post by ianb72 on 2007-11-13
> **skanchi said:**
> Before you request for an IP address, check the wireless link is up. type dmesg, and check for link up message. 
Other things to check are the association to the AP. Issue the command "iwconfig wlan0"

Hi There,
Mike is my dad and we have managed to get his wireless working just great WITHOUT any WEP.

But as soon as we put his hex WEP key in and we type the following 
[HTML]mike@mike-desktop:~$ sudo dhclient wlan0 [/HTML]

We get the following 
[HTML] [sudo] password for mike:
There is already a pid file /var/run/dhclient.pid with pid 6741
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:12:17:97:84:bb
Sending on   LPF/wlan0/00:12:17:97:84:bb
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
mike@mike-desktop:~$[/HTML]

Can anyone tell me whats wrong and what the following is all about?

[HTML]There is already a pid file /var/run/dhclient.pid with pid 6741
killed old client process, removed PID file [/HTML]

We would be very grateful for any info that could get my dads wireless working with WEP or even WPA.

Cheers
Ian

---

