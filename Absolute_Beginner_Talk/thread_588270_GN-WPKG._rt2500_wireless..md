---
title: "GN-WPKG. rt2500 wireless."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-10-23
Okay.  Here's the issue.  I have a GN-WPKG PCI card.   Please tell me, is this natively supported in Ubuntu 7.04 feisty?  It uses the rt2500 chipset and I thought it was.

I plugged it in and turned on the computer and I try to connect, it says "connected" but I can't get on the internet. No net connection.    I try to enable the device with

```

sudo dhclient ra0

``` 

And it gives me a whole heap of crap and at the end tells me it's sleeping.

Please, can somebody gimme some terminal commands to try so we can distinguish the exact cause of the problem so it can be fixed? This is quite urgent, if you're reading this, please for the love of God, post something.  D:

And, just a sub question, on version 7.10, will this work, as advertised, "out of the box"? Because "out of the box" isn't agreeing with Feisty Fawn.

---

### Post by Daveth on 2007-10-23
I cannot obviously see it here

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

this post got it sorted, though not a walk in the park

[http://www.linuxquestions.org/hcl/showproduct.php/product/2600/si/WiFi/perpage/15/sort/2](http://www.linuxquestions.org/hcl/showproduct.php/product/2600/si/WiFi/perpage/15/sort/2)

Gutsy is supposed to have much better wireless support.....

---

### Post by Neon_Knight on 2007-10-24
> **Daveth said:**
> I cannot obviously see it here

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

this post got it sorted, though not a walk in the park

[http://www.linuxquestions.org/hcl/showproduct.php/product/2600/si/WiFi/perpage/15/sort/2](http://www.linuxquestions.org/hcl/showproduct.php/product/2600/si/WiFi/perpage/15/sort/2)

Gutsy is supposed to have much better wireless support.....

It is, under gigabyte, it says it works "out of the box", highly recommended.

And I'll have a look at that second link, thanks.

Edit:  Uhhhh that second link is extremely confusing... any "absolute beginner talk" versions, or translations? D:

---

### Post by Neon_Knight on 2007-10-24
Okay, here's what it says:

```

erin@erin-desktop:~$ sudo dhclient ra0

Password:

Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/



Listening on LPF/ra0/00:0f:ea:68:d3:e9

Sending on   LPF/ra0/00:0f:ea:68:d3:e9

Sending on   Socket/fallback

DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6

DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

erin@erin-desktop:~$ 

```

---

### Post by bikeboy on 2007-10-24
Hi there, rt2500 was indeed a problem on Feisty, although the driver itself was fine. Unfortunately, while Gutsy has made progress it has also made backwards steps.

I welcome you to try the [solution](http://www.vickersf.dyndns.org:8080/blog/2007/07/03/howto-ralink-ubuntu-feisty/) that worked for me, which involves turning the device off while applying some settings, then bringing it back up. Don't worry, it's easier than it sounds and the guide makes it happen automatically during boot up.

Hope it helps.

---

### Post by Neon_Knight on 2007-10-24
Hi, thanks so much for the link,  I'll be doing that.   But, do you know if I actually HAVE to uninstall network manager?

---

### Post by bikeboy on 2007-10-24
I don't remember if you have to, but the driver in Feisty won't work through NM. That is, NM will be non-functional as far as your wireless goes, even if it's installed.

---

### Post by Neon_Knight on 2007-10-24
> **bikeboy said:**
> I don't remember if you have to, but the driver in Feisty won't work through NM. That is, NM will be non-functional as far as your wireless goes, even if it's installed.

Right, well thanks alot for that.   

I'll be trying that and responding with the output.

---

### Post by bikeboy on 2007-10-24
No probs,

Look forward to a *hopefully* good outcome.

---

### Post by Neon_Knight on 2007-10-24
Bad news, people.

```

erin@erin-desktop:~$ cd /etc/init.d/
erin@erin-desktop:/etc/init.d$ sudo chmod o+x ./wireless-up
erin@erin-desktop:/etc/init.d$ cd /etc/rc2.d/
erin@erin-desktop:/etc/rc2.d$ sudo ln -s /etc/init.d/wireless-up ./S14wireless-up
ln: creating symbolic link `./S14wireless-up' to `/etc/init.d/wireless-up': File exists
erin@erin-desktop:/etc/rc2.d$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]
erin@erin-desktop:/etc/rc2.d$ 

```

What am I doing wrong?    Thanks.


I've restarted and it won't go online.

---

### Post by bikeboy on 2007-10-25
Looking at the messages there I don't see an entry for ra0 like I would expect. You could try making sure NM isn't running at the time by doing 'killall NetworkManager'. Then restart the networking. Otherwise, I wonder if any changes have been made to /etc/network/interfaces so that ra0 isn't listed or something.

---

