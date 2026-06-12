---
title: "No Internet Connection at All."
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by AlphaMack on 2006-01-07
Dell Inspiron 4100, completely OEM

Hi,

When I installed Ubuntu via CD, it was not connected to DSL/Cable.  Now when I try to enable eth0 and connect using DHCP, it will insist on using lo with my local IP (127.0.0.1).

I disabled IPv6 via Firefox and by uncommenting it in /etc/modprobe.d/aliases.

I also tried creating a location with the default gateway set to eth0 but for some reason Ubuntu will not remember this.  A quick look at the connection in the upper right corner continues to show lo.

TFM doesn't seem to be helping, so I'm wondering if there's someone out there who can point me the right way into getting the Internet to work.

---

### Post by alamba on 2006-01-07
This might be on the wrong track, but if u're saying it insists on using lo by only looking at the connection icon on the upper left hand corner...try this...

Click the icon on the top left hand corner...click on the drop down menu called name...and choose eth0!!

If eth0 does'nt show up..then we need to troubleshoot some more to figure out what's happening. Paste your ifconfig.

Akshay

---

### Post by AlphaMack on 2006-01-07
[QUOTE=alamba]This might be on the wrong track, but if u're saying it insists on using lo by only looking at the connection icon on the upper left hand corner...try this...

Click the icon on the top left hand corner...click on the drop down menu called name...and choose eth0!!

If eth0 does'nt show up..then we need to troubleshoot some more to figure out what's happening. Paste your ifconfig.

Akshay[/QUOTE]


Awesome...I don't know why I didn't think of that.

I went back into System>Administration>Networking and once again it doesn't remember my location name or default gateway device (eth0) -- they're both blank selections.


Here is the output from ifconfig (as retyped):

eth0

Link encap:Ethernet HWaddr 00:06:5B:36:3E:A6
inet6 addr:  fe80::206:5bff:fe36:3ea6/64 Scope: Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:25310 errors:0 dropped:0 overruns:1 frame:0
TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1532196 (1.4 MiB) TX bytes:37134 (36.2 KiB)
Interrupt:ll Base address:0xec80

lo

Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:18722 errors:0 dropped:0 overruns:0 frame:0
TX packets:18722 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1704259 (1.6 MiB) TX bytes:1704259 (1.6 MiB)

---

### Post by AlphaMack on 2006-01-07
Hmmm...the network icon in the upper right corner?  "lo" is the only thing available in the drop down menu.  eth0 is nowhere to be found.

I also went back and re-enabled IPv6.  I've tried rebooting.  Nothing seems to work.

---

### Post by AlphaMack on 2006-01-07
Okay...I feel really stupid for this, especially after seeing that the eth0 was configured correctly...


...I forgot to restart the cable modem!  :razz: 

I'm now posting from Ubuntu.  :KS

---

