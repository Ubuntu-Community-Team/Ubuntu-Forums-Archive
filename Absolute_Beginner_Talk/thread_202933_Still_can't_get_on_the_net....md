---
title: "Still can't get on the net..."
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by mistrip on 2006-06-24
Ok, i thought i'd start from scratch and try the 32bit version of ubuntu 6.06.

This seems to have fixed another problem where i couldn't access data on any of my windows partitions :)   The media player doesn't seem to have the required codecs for MP3s at first install...is this normal?  If so it seems a bit of an oversight given their poularity.

Anyway, back to my main problem...

I'm connected to the net with a cable modem (via telewest blueyonder), hooked up to the onboard nvidia NIC via ethernet.  I have tried disabling and re-enabling eth0 but this doesn't fix it.  None of my applications can access the net so it doesn't seem to be specific to one program.

Any ideas:confused:   Please make you replies smple though as this is my first attempt with linux.

Thanks

[edit] I might aswell post my other problem here too:

On trying to install the nvidia graphics drivers and nforce driers i get the message, "please make sure you have the package binutils installed and then please check that ld is in your PATH. Any ideas on this one?

---

### Post by mistrip on 2006-06-24
Woot!  My cable modem has an option for a usb connection so i tried that and it worked first time :D I'd prefer tio use the ethernet one but i'm willing to live with usb.

Anyone got any ideas on the nvidia driver problem though?

---

### Post by cskeide on 2006-06-24
Because of its commitment to only include completely free software by default, Ubuntu does not support proprietary media formats (such as mp3) 'out of the box'. Read [RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats") for more information.

Network problem:
First, some questions: Do you have a static ip address, or does your modem/router also work as a DHCP? Have you configured your device accordingly?
1. Open up a terminal (Applications -> Accessories -> Terminal)
2. Copy the output of these commands and post it here:```
cat /etc/network/interfaces
ifconfig -a
```

Nvidia problem:
Have you read [this]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html")? Don't have a nvidia card myself, but can't see why you would need binutils... Anyways, this should fix your error-message:
1. Open up a terminal
2. Install build-essential```
sudo apt-get update
sudo apt-get install build-essential
```

Hope this helps.

---

### Post by mistrip on 2006-06-24
When i type this....cat /etc/network/interfaces
ifconfig -a

The result is this:
[I]auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

iface dsl-provider inet ppp
provider dsl-provider
pravin@Thermaltake:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:F2:52:DB:83
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225

eth1      Link encap:Ethernet  HWaddr 00:11:E6:5C:32:C4
          inet addr:82.33.126.251  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::211:e6ff:fe5c:32c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:162671 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:174446888 (166.3 MiB)  TX bytes:4458250 (4.2 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[/I]
At the moment i'm using eth1 for my net connection as my modem has both USB and ethernet.  It's when i use the ethernet connection (eth0) that i have the problem.

---

