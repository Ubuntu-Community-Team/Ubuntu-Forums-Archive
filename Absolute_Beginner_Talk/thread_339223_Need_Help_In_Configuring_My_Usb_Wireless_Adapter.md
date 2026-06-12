---
title: "Need Help In Configuring My Usb Wireless Adapter"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by wise_1 on 2007-01-15
Hello all,
I'm new to the Ubuntu. Actually, I'm quite new to linux.  I'm trying to get my usb wireless to work and so far, I have not been able to.  Any help that I can get from anyone out there will be extremely appreciated..

wise..

I'm using  a Belkin Wireless G USB Network Adapter part#  F5D7050

xxxx@xxxx-desktop:~$ iwconfig 
lo        no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.462 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"xxxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
eth0      no wireless extensions.

sit0      no wireless extensions.


INTERFACE INFO
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wmaster0 inet dhcp
wireless-essid PDD

auto eth0

iface wlan0 inet static
wireless-essid xxxx
address 172.16.1.36
netmask 255.255.0.0
gateway 172.16.0.1

auto wlan0
auto wmaster0

iwconfig -C network
 *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:23:34:c1:0d:0b
       capabilities: ethernet physical wireless
       configuration: ip=172.16.1.36 multicast=yes wireless=IEEE 802.11g

---

### Post by peabody on 2007-01-15
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Doing a search for your card on that page does seem to indicate that your stick can be made to work with NDIS wrapper (a utility that can be used to make the windows wireless drivers work with Linux).

The wiki documentation for ndiswrapper is here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

If those documents give you trouble let us know, feel free to ask questions.

---

### Post by wise_1 on 2007-01-15
Thanks for the info. I will take look at it and hopefully figure it all out...

wise_1

---

### Post by wise_1 on 2007-01-15
I'm still having a little problem understanding exactly what I'm supposed to do here:  what 
does the user below means when he says "install the drivers for windows included in the box and fetch the .inf and .sys fyles from the installation directory."  How do you install the windows drivers? what does he mean by fecthing the .inf and .sys files from the installation directory?

Thanks in advance
Wise_1

Card: Belkin F5D7050 (USB 2.0 Adaptor 802.11g 54Mbps) 
Chipset: Conexant (PrismUSB) 
usbid: 050D:7050 
Driver: Install the drivers for windows included in the box and fetch the .inf and .sys fyles from the installation directory. 
Other: linux-2.6.9: Blocks Linux momentarily when another device is plugged into the same USB Hub, more precisely a 1.1 memory stick. 
Other: SuSE 9.1, kernel-2.6.8-default (kernel-of-the-day 22 Dec. 2004): 1.0rc1 with bknUSB.inf from the vendor CD and WEP security works quite stable. The procedure as described in WiKi/SuSE 9.1. Professional. 
Other: SuSE 9.1, kernel-2.6.x-smp: doesn't work, 'modprobe ndiswrapper' freezes the system.

---

### Post by peabody on 2007-01-15
Don't pay much attention to the first link, It was just the first thing I ran across to determine whether the card could even be made to work.  The second link is what you want to pay attention to.

---

### Post by wise_1 on 2007-01-15
I'm following the second LINK you listed in your first post..
I get all the way to step 8.2.3
and when I issue the command: sudo ifdown wlan 0", I get the following error:

There is already a pid file /var/run/dhclient.wlan0.pid with pid 4694
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:be:0d:0b
Sending on   LPF/wlan0/00:11:50:be:0d:0b
Sending on   Socket/fallback

Note: I only have one wireless usb stick installed on this PC, but the system seem to recognise two:  wmaster0 and wlan0. Is this normal?

---

### Post by peabody on 2007-01-16
> **wise_1 said:**
> 
Note: I only have one wireless usb stick installed on this PC, but the system seem to recognise two:  wmaster0 and wlan0. Is this normal?

I don't know, I don't have that hardware.  Can you ping anything?

---

### Post by wise_1 on 2007-01-16
No, I'm getting network unreachable.....
I can ping the loopback...127.0.0.1

---

### Post by peabody on 2007-01-16
> wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801

Hmm, it could be this type of adapter can be used for an ap and this would be the name of the interface to use for it.  These messages seem to indicate it's not working, so I think you should just ignore wmaster0 and focus on wlan0.

Also, while it's rare, there are some open source drivers that interfere with ndiswrapper for certain makes and models of card.  It's possible to fix the problem by blacklisting the open source modules.  I'd have to look into that however (and it's likely not your problem).

Are you able to try and manually configure the device through the network interface panel?

---

### Post by wise_1 on 2007-01-16
Do you know how I can get wlassistant or network-manager to work? Currently, it doesn't look like I have them installed?

wise

---

### Post by peabody on 2007-01-16
Well, without a network connection that could be a problem as I'm not sure just getting the debian package would be enough (probably has multiple dependencies).

Isn't there a control panel of some sort in Edgy to manually configure things like WEP key etc.?

---

### Post by wise_1 on 2007-01-16
Edgy has a generic networking dialog setting that allow network configuration. However it's very generic and it doesn't have all the options needed, and  you have to edit the interfaces file.  

As far as wlassistant.. I downloaded a package from 
[https://sourceforge.net/project/downloading.php?group_id=134488&use_mirror=superb-east&filename=wlassistant-0.5.6-i386-1.tgz&18977129](https://sourceforge.net/project/downloading.php?group_id=134488&use_mirror=superb-east&filename=wlassistant-0.5.6-i386-1.tgz&18977129)

I unzipped it...and the install file has a .sh extension. I try to run it from the command line..and it's not working... Is there a way to get this .sh executable to run in edgy.

Note: I apppreciate all your help and suggestions...whether I get it to work or not..

wise...

---

### Post by tagginannie on 2007-01-16
> **wise_1 said:**
> Hello all,
I'm new to the Ubuntu. Actually, I'm quite new to linux.  I'm trying to get my usb wireless to work and so far, I have not been able to.  Any help that I can get from anyone out there will be extremely appreciated..

wise..

I'm using  a Belkin Wireless G USB Network Adapter part#  F5D7050 


Hi Wise

This Wiki should help you

WifiDocs/Device/Belkin F5D7050 ver 3000 (Ralink rt73 driver)
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?action=show)

Suzy

---

### Post by wise_1 on 2007-01-16
[COLOR="Blue"]Thanks Suzy, [/COLOR]
You are my savior, I finally got it.  After following the instructions on your link, I was able to get it...Thank you..  I spent countless hours during the last couple of days trying to get this working and your link was all that I needed.  Thank you...thank you ...thank you

and Pea thanks again  for your help....

Best wishes to both of you

Wise...

---

