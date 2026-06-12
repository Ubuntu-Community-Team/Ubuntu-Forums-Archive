---
title: "iBook Airport Extreme works &quot;sometimes&quot;"
date: 2006-08-02
forum: Apple PPC Users
---

### Post by cherrysmooth on 2006-08-02
Hi All,

Hopefully I am not the only one that has seen this.  

I have been trying to get my AE working with my home network.  I followed the firmware upgrade (fwcutter) instructions and had some success.  I say some because sometimes I see the network, sometimes I dont.  It seems like when I run iwlist scan I can see my home network without fail. But I don't always connect to it.  The network admin will say the card is active, but it is not resolving its ip address through dhcp.  So i turned that off and put in a static ip, still no luck.

Help...

---

### Post by eidex on 2006-08-02
Same problem here, i can alway see the wireless networks and connect to them (iwconfig shows essid and mac of wlan router, but dhclient often fails), networkmanager is more likely to fail or needs more than one atttempt to connect than if i connect manually (or by script shown in the wiki)

btw networkmanager alway takes very long to connect  (30secs and more), the scripts establish a connection in a second or so...

---

### Post by rasec on 2006-08-02
cherrysmooth, are you trying to connect to a wpa encrypted network? If you are, I suggest that you use the wpa_supplicant method to connect the network because network manager for the powerpc can't handle wpa networks currently (unless you want to recompile it). There should be a wiki article over at ubuntu.com to help you configure it.

eidex, network manager is slow for me, too, but at least it always seems to work.

---

### Post by cherrysmooth on 2006-08-03
No I have turned off the encryption to my network to see if I can get this working.

eidex, my network manager takes forever too? sometimes i can get the network connection working, but its after i run the iwlist scan command a couple of times?

any ideas anyone?

---

### Post by rasec on 2006-08-03
How's your reception? A low signal strength might explain why you are having problems connecting.

---

### Post by cherrysmooth on 2006-08-03
The signal strength is 100/100.  My workspace and wireless router are located in the same room.  Not sure if it makes a difference but the last time I got it working I hooked in an ethernet cable, activated that, then activated the wireless and it received properly.  Then foolish me said to myself this cant be coincidence and rebooted to see if the wireless worked, no joy.

---

### Post by rasec on 2006-08-03
I don't think you can have 2 network connections working at the same time, so odds are that you were still using your ethernet connection, unless you unplugged the cable.

Anyway, why don't you try setting up the wireless network manually and then you can try getting network manager working. Here's how to connect to an open wireless access point names AP. These changes belong to your /etc/network/interfaces:

```

auto eth1
iface eth1 inet dhcp
    wpa-ssid AP
    wpa-key-mgmt NONE
    wpa-driver wext

```

After you modify your interfaces file, do a "sudo /etc/init.d/network restart" and you should be able to connect to your network.

---

### Post by cherrysmooth on 2006-08-03
No Joy, looks like it cant see the network, I attached the output below.  But if I run the iwlist scan command it sees the network fine.

<code>
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0d:93:88:b3:4c
Sending on   LPF/eth0/00:0d:93:88:b3:4c
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0d:93:88:b3:4c
Sending on   LPF/eth0/00:0d:93:88:b3:4c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
</code>

<code>
lo        Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:09:5B:53:8F:00
                    ESSID:"HOME"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-141 dBm
                    Extra: Last beacon: 64ms ago

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.
</code>

---

### Post by rasec on 2006-08-03
It looks like I got your airport device name mixed up with your ethernet card. Why don't you modify the example interfaces I gave above by replacing eth1 with eth0.

Another thing you can try is to explicitly associate with the access point directly by:

```

sudo iwconfig eth0 essid HOME
sudo dhclient eth0

```

That should work, but I didn't test it.

By the way, use [] for code and quote blocks, not <>.

---

