---
title: "My Wireless Problems"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by shambotics on 2007-03-07
Good morning,

This is my first post here, so before I get started I want to say that I am impressed and encouraged by the amount of help being doled out to us noobs by the community.  Browsing this forum gave me the courage to go ahead with my Ubuntu install.

Overall, things have gone very well.  The install went fine, and I was online (wired) right away.

My problem, like several others here, is my wireless configuration.

After failing to get the wireless card to connect to my AP through the Network control panel, and after reading a lot of threads on this forum, I followed the directions posted [here](http://www.ubuntuforums.org/showthread.php?t=346083) by Kolbalt.  Things went fine setting up ndiswrapper, but I still cannot connect.

I have a feeling that this is some kind of noob pilot error on my part, and I'm hoping that one of you guys can help me out.

Below is the ouput of various commands that I have seen requested in other threads:

lspci returns a long list including:
```

02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

```

iwconfig returns:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

sudo ifdown eth1 returns:
```

There is already a pid file /var/run/dhclient.eth1.pid with pid 5050
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0b:7d:26:6c:77
Sending on   LPF/eth1/00:0b:7d:26:6c:77
Sending on   Socket/fallback

```

sudo ifup eth1 returns:
```

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Invalid argument.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0b:7d:26:6c:77
Sending on   LPF/eth1/00:0b:7d:26:6c:77
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

The error here might be my problem, but I'm not sure what to do about it.  It seems to be related to my network password.  I know that the password is correct, and I have tried it with Password Type set to both Plain and Hex.

ndiswrapper -l returns:
```

bcmwl5a : driver installed
        device (14E4:4324) present (alternate driver: bcm43xx)

```

Note: I initially used the driver specified in Kolbalt's post.  When that didn't work, I tried the driver specified for my card by the list on the ndiswrapper wiki.  Hence the 'bcmwl5a'.

I'm sure I have left some information out.  Let me know what you need and I'll post asap.

Thanks in advance!

---

### Post by solar george on 2007-03-07
Add the following to a new line at the bottom of your /etc/modprobe.d/blacklist file
```
blacklist bcm43xx
```

Then reboot.

---

### Post by shambotics on 2007-03-07
> **solar george said:**
> Add the following to a new line at the bottom of your /etc/modprobe.d/blacklist file
```
blacklist bcm43xx
```

Then reboot.

Thanks for responding.

I double checked and I had already added that line to the blacklist file as per Kolbalt's instructions in the thread linked in my first post.  I have rebooted several times since.

I'm starting to wonder if this is a problem with my encryption type.  My AP is set to use WPA-PSK with cypher type TKIP.  Is all that supported or do I need to change it?

Thanks!

---

### Post by solar george on 2007-03-07
Wpa is awkward. Try [this]("http://www.ubuntuforums.org/showthread.php?t=373487&highlight=wpa")

---

### Post by shambotics on 2007-03-07
> **solar george said:**
> Wpa is awkward. Try [this]("http://www.ubuntuforums.org/showthread.php?t=373487&highlight=wpa")

Posting over wireless!  Thank you!

---

