---
title: "Ubuntu gone, GRUB problem"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by calford on 2007-08-14
Hi,
My motherboard died and i had to get a new one, after the change Ubuntu wont load anymore.
I use GRUB and it just hangs there doing nothing if i choose Ubuntu or Windows.
I have Ubuntu installed in an IDE HD and XP in a SATA HD.

I tried to use a live CD to fix the problem but i get an error message about tty being turned off or something like that.

I can access my Ubuntu hard drive from Windows and everything is in there, i just can boot from it.

how can i fix the grub?

thanks

---

### Post by nvrpunk on 2007-08-14
What probably happened is the devices are populating in a different order now.  So Harddrive lets say A was /dev/sda or /dev/hda it may now be /dev/sdb or /dev/hdb.  You need to boot onto the livecd and figure out which is which using fdisk but making no changes.  You can then just edit the /boot/grub/grub.conf or you may have to plug your drives in a different order on the mobo.  

-nvrpunk-

---

### Post by guguma on 2007-08-14
If you have an alternate install cd, choose rescue option.

Then after it configures your network and so, choose reinstall Grub. It MAY work. But you can also continue after installing grub. Choose execute a login shell, and choose the partition where ubuntu is installed. It will give you an ugly shell. Just type 

```
startx
```

and then check your /etc/fstab and /boot/grub/grub.conf.

if everyhting seems OK, reboot. Also you can post the contents of the fstab and grub.conf.

---

### Post by calford on 2007-08-16
thanks guys,
i managed to start ubuntu again by going into my old GRUB and changing some  numbers.
It started after few error messages (ata3.0 and ata3.1).
everything seems OK but i have no network.
How can i set the network up again?

---

### Post by oilchangeguy on 2007-08-16
> **calford said:**
> thanks guys,
i managed to start ubuntu again by going into my old GRUB and changing some  numbers.
It started after few error messages (ata3.0 and ata3.1).
everything seems OK but i have no network.
How can i set the network up again?

i suggest that you backup any data you may have, and do a fresh install.

---

### Post by calford on 2007-08-16
thanks for your answer oilchangeguy
i was fearing that.
is there no other way of fixing the networking issue?

---

### Post by bodhi.zazen on 2007-08-16
Can you give us some more information regarding you network problem ?

What happens if you start the network ?

```
sudo /etc/init.d/network restart
```

What if you start the device manually ?

```
sudo ifup eth0
``` 

or

```
sudo dhcpclient eth0
```

---

### Post by calford on 2007-08-17
this is what i get

sudo /etc/init.d/network restart

RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 7670
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1a:4d:45:6b:e3
Sending on   LPF/eth1/00:1a:4d:45:6b:e3
Sending on   Socket/fallback
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1a:4d:45:6b:e3
Sending on   LPF/eth1/00:1a:4d:45:6b:e3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

for :sudo ifup eth0

Feth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

for: sudo dhcpclient eth0
i get a command not found error message

thanks

---

### Post by bodhi.zazen on 2007-08-17
Are you on wireless ?

Can you post the content of /etc/network/interfaces ?

Is network manager working ?

---

### Post by calford on 2007-08-17
nope, not on wireless

/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1


network manager?

---

