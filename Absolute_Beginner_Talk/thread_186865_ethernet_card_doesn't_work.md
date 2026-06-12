---
title: "ethernet card doesn't work?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by nyara on 2006-06-02
So I took my computer to a coffee shop yesterday and while I was on the wireless I installed some new updates.  When I got back to my land line I can't connect to any sites despite the fact that network-admin shows I'm connected.  What's the deal?

---

### Post by murph2481 on 2006-06-02
Do you have an ip address?

Try typing 'ifconfig' at the command line.  If you do not have a ip address try typing 'sudo dhclient'

---

### Post by Iowan on 2006-06-02
I wonder if the gateway, DNS, DHCP (or other important setting) got set for the wireless, and now (although connected), the wired side is lost/confused?

---

### Post by nyara on 2006-06-02
That seems really possible.  The error I am getting says:

No DHCPOFFERS received
No Working leases in persistent database - sleeping

---

### Post by nyara on 2006-06-02
I've tried setting up a static IP and then switching back from this thread.
[http://ubuntuforums.org/showthread.php?t=182618](http://ubuntuforums.org/showthread.php?t=182618)

That didn't work.

I also tried blacklisting tulip from this thread.
[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

Didn't work either :(

---

### Post by murph2481 on 2006-06-02
here is a dumb question, but a legit one.  Is the card enabled?  I had to enable my ethernet connection but i didn't have to do that for my wireless.

---

### Post by usernamed on 2006-06-02
[QUOTE=nyara]That seems really possible.  The error I am getting says:

No DHCPOFFERS received
No Working leases in persistent database - sleeping[/QUOTE]


If you open System->Networking, what does it say your default gateway is?

Also, please print the output from 'ifconfig' and 'route'  (route may take a little while if your routing is confused)

---

### Post by nyara on 2006-06-02
Yeah, it's enabled, I've tried checking and unchecking that button a few times to see if that changes anything.

---

### Post by nyara on 2006-06-02
route says

Kernel IP routing table
Destination         Gateway          Genmask            Flags  Metric   Ref           Use  Iface
192.168.1.0        *                      255.255.255.0    U           0          0                  0  eth0
default                192.168.1.1     0.0.0.0                UG        0         0                   0  eth0      

ifconfig says 

eth0        Link encap:Ethernet     HWaddr 00:12:3F:D1:9F:3B
               inet addr:192.168.1.105   Bcast:192.168.1.255   Mask:255.255.255.0
               inet6 addr:  fe80::212:3fff:fed1:9f3b/64  Scope:Link
               UP BROADCAST RUNNING MULTICAST    MTU:1500   Metric:1
               RX packets:82379 errors:0 dropped:0 overruns:0 frame:0
               TX packets:5994  errors:0 dropped:0  overruns:0 carrier:0
               collisions:0 txqueuelen:1000
               RXbytes:17327718  (16.5 MiB)    TX bytes:385134   (376.1 KiB)
               Interrupt:209

and then it has eth1

my default gateway is eth0

---

### Post by Iowan on 2006-06-02
[QUOTE=nyara]eth0 Link encap:Ethernet HWaddr 00:12:3F1:9F:3B
inet addr:192.168.1.105 Bcast:192.168.1.255 Mask:255.255.255.0[/QUOTE]Did you manually assign the address to eth0 - or did it manage to find one? 
Is the DNS server still the one you set?
Do you have a router at 192.168.1.1 or should this be your ISP?

---

