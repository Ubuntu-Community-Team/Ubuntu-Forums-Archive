---
title: "problems connecting to internet"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Pulka on 2008-01-21
hello everyone!

Again, connecting to internet is always a nightmare in Linux.

Have an active wireless connection, but can't seem to be able to connect it. Here's some configuration:

**iwconfig**

lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"xxxx"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[B]
iwlist wlan0 scanning[/B]
wlan0     No scan results


**sudo ifdown wlan0**
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5278
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:11:bf:63:b6
Sending on   LPF/wlan0/00:1b:11:bf:63:b6
Sending on   Socket/fallback
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
cxxx@cxxxx-desktop:~$ sudo ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

[B]
/etc/network/interfaces[/B]
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-essid xxxx

auto wlan0


does anyone has a clue why i can't connect?

---

### Post by OffAxis on 2008-01-21
try this
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by Kulgan on 2008-01-21
You replaced your ssid with "xxxx" - if it's "default" - which is the default... ha, ha, ha... on some routers, change it. For some reason there are issues. 

Also, you may want to just get rid of everything in the /etc/network/interfaces file exept the loopback lines. Then you use the network manager applet with a "clean slate". 

After you have done that and rebooted, post the output of "ifconfig" and "iwlist scanning" - without interface names. Of course you should make sure that the wireless is completely unsecured when troubleshooting, as the guide says. 

-K

---

### Post by Thund3rstruck on 2008-01-21
I had similar problems on an old laptop but I just installed NetworkManager and it took care of everything for me

---

### Post by rosegarden78 on 2008-01-21
Try typing **nm-applet** from a terminal.

---

### Post by Kulgan on 2008-01-22
to use that in kde, install network-manager-kde from the repos. that way you also have the icon setup working.

Edit: 
Sorry, I'm posting the reply to a question in another topic. Ignore that. nm-applet (package network-manager and network-manager-gnome) should be installed by default, so I presume that you have not been able to get it to work using that. Of course, if for some reason it's not installed, you will want to install that :D

Sorry for the mis-post

---

### Post by Pulka on 2008-01-23
I use wi-fi radar. 
It detects my wireless card, already configured my essid, but i can't get no IP.
Yesterday i managed to connect manually, configuring the channel and the Access Point, but after the updates, not even that way

---

### Post by Pulka on 2008-01-23
nevermind...solved it with this command:

  "sudo dhclient <ath0>"

---

