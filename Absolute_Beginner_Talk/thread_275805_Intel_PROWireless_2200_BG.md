---
title: "Intel PRO/Wireless 2200 BG"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by brensel147 on 2006-10-11
I have one more issue.  My intel wireless card is built into my laptop.  It was working fine and I got the wpa_suplicant to work but when I upgraded the kernal network manager couldn't even find any wireless signals.  It still seems to be working I just can't configure it with Network manager or make the wpa work.  What should I do?

---

### Post by John.Michael.Kane on 2006-10-11
Did you try the method that got it working the frist time before the kern upgrade?

Sometimes you have to reconfigure your net setup after a kern-upgrade.

---

### Post by brensel147 on 2006-10-11
I just redid all of it and the network manager still isn't showing anything but the wired connection.  I even tried using wifi_radar but it doesn't seem to work either.  Not sure where to go from here?

---

### Post by drr422 on 2006-10-11
the same thing is happening with my card (which is the same as yours)  as well, i just kind of ignored it cause I'm thinking that wifi_radar is taking care of it for me.  Knetworkmanager doesn't detect the wifi network, only the wired one, but my other utilities such as wifi_radar and Wireless assistant work though.

Dustin

---

### Post by regx on 2006-10-12
I have had problems with the built in wireless tools in Ubuntu since hoary. Dapper, edgy ... same story.](*,) 

I think it has to do with the command execution order, or maybe something is just missing. I have the same problems in debian, and this works there as well.

Assuming your driver is installed, and you can you see it listed when type ifconfig from the command line, try this.a

ifconfig rausb0 down
ifconfig rausb0 up
iwconfig rausb0 mode managed
iwconfig rausb0 key open 5E52CB31E2B8BE834FFE127EEF
iwconfig rausb0 essid 'linsys'
dhclient rausb0

replace rausb0 with your wireless device id from ifconfig
mode can be either open or managed
change the eesid and wep as appropriate.

if that works for you make a shell or perl script.

#!/usr/bin/perl -w
use strict;
`ifconfig rausb0 down`;
`ifconfig rausb0 up`;
`iwconfig rausb0 mode managed`;
`iwconfig rausb0 key open 5E52CB31E2B8BE834FFE127EEF`;
`iwconfig rausb0 essid 'linksys'`;
`dhclient rausb0`;


So far this hasn't failed me on three laptops across 3 distros.
I don't think I have ever had the pre-installed utils work.

If you do not see your device in ifconfig, and can't find a driver see ndiswrapper

only other problem I have ad was with the default driver for hp broadcom bmcxxx in dapper. Had to blacklist a module to get ndiswrapper to work.

Hope this helps someone out.

---

