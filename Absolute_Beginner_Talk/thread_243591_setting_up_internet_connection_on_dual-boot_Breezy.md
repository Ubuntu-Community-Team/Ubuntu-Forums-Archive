---
title: "setting up internet connection on dual-boot Breezy laptop"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by pfctdayelise on 2006-08-25
Hello,

Problem: Unable to connect to internet via Ethernet NIC.

Stats: Breezy Badger dual-boot with WinXP on a NEC VERSA S940. NIC is RealTek RTL8139/810X Family First Ethernet NIC which is listed here : [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards)

According to the HOWTO ( [http://www.ubuntuforums.org/showthread.php?t=86389](http://www.ubuntuforums.org/showthread.php?t=86389) ), the first thing I want to do is run ifconfig. When I run this it has no output whatsoever. Same if I run it sudo.

When I go to System > Administration > Networking, I get a thing in the bottom panel saying "Starting Networking..." and the mouse changes as if it is waiting for the program to start, but then it just disappears and nothing new opens. (This actually happens when I try to open several other things in that menu, e.g. Login Settings).

The internet works fine when I boot with Windows. :(

When I plug in the cable, the light comes on as it does with Windows.

When I run mii-tool, it says:

SIOCGMIIPHY on 'eth0' failed: Operation not permitted
(ditto up to eth7)
no MII interfaces found

So, what am I missing, what's going on? Bad install? I'd really like to upgrade to Dapper...

cheers and thanks in advance

Brianna

---

### Post by pfctdayelise on 2006-08-26
...Anyone got any ideas at all??? :-k

---

### Post by Skia_42 on 2006-08-26
I doubt it's a bad install, you aren't behind a router are you?

---

### Post by pfctdayelise on 2006-08-26
> **Skia_42 said:**
> I doubt it's a bad install, you aren't behind a router are you?

Actually, I am, although I only just realised. There's a little white box outside my bedroom that says cable/DSL router. :)

It's a [Netgear RP614v3 4 Port Cable or DSL Router with 10/100 Mbps Switch]("http://kbserver.netgear.com/products/rp614v3.asp"). So there you go.

---

### Post by pfctdayelise on 2006-08-28
So.......any more tips?? It seems pretty odd that ifconfig has no output whatsoever.

---

### Post by pfctdayelise on 2006-09-03
anyone, anyone, anyone..........:KS

---

### Post by Sef on 2006-09-03
Do you have a breezy live cd, so you can check out breezy.  It could be the install went bad and that is why the problem exists.  If the live cd connects to the net, I would say that is the problem.

---

### Post by pfctdayelise on 2006-09-03
Hmm.... I do, but it takes forEVER to load.

I was hoping to solve this so I could easily upgrade to Dapper, actually.

---

### Post by goatflyer on 2006-09-03
It seems more likely that your network card isn't being detected -- despite the advertisement.  At this stage I would bypass Breezy altogether and try a fresh install of Dapper.

---

### Post by Brunellus on 2006-09-03
please post the complete output of 

ifconfig -a

there should be an eth0 there.  if it is there, and it's not activated, then bring it up with

sudo ifup eth0

that should bring the interface up.

---

### Post by pfctdayelise on 2006-09-04
OK, it was listed in ifconfig -a:

eth0
Link encap: Ethernet Hwaddr 00:C0:9F:9B:B1:C8
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) 
Interrupt:5 Base address:0x3000

There's also eth1, lo, sit0.

Hmm... lots of zeros.

that was after running 'sudo ifup eth0' (which had no external effect, to me).


Also, when I reboot with the cable in, it's the same excepy the Hwaddr is 00:12:F0:73:3A:94

and the last line says 

Interrupt:10 Base address: 0xe000 Memory: e020600-e0206fff

---

