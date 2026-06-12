---
title: "PacketGarden help"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by yuvlevental on 2007-06-28
I'm trying to run packetgarden, but i get this error:
<code>
* Soya Pudding * Version: 0.1-0
  File "/usr/share/games/packetgarden/pg_packet.py", line 21, in <module>
    import pcap
ImportError: No module named pcap
</code>
I checked in synaptic and found i had pcap. What could I be doing wrong?

---

### Post by arhhook on 2007-07-26
I am having the same problem as well when i try to capture eth1.

Wireless interface: eth1
ipw3945

Kubuntu Feisty Fawn 7.01

> 
anthony@h00kb0x:~$ packetgarden
config  data  guide  labels  logs  stats
user directory already exists
* Soya * Using 8 bits stencil buffer

* Soya * version 0.12
* Using OpenGL 1.3 Mesa 6.5.2
*   - renderer : Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
*   - vendor   : Tungsten Graphics, Inc
*   - maximum number of lights        : 8
*   - maximum number of clip planes   : 6
*   - maximum number of texture units : 8
*   - maximum texture size            : 2048 pixels

* Soya Pudding * Version: 0.1-0
  File "/usr/share/games/packetgarden/pg_packet.py", line 21, in <module>
    import pcap
ImportError: No module named pcap


Has anyone found any help?

I have installed pypcap_1.1, dpkt_1.6, and packetgarden_1.0pre8.

---

### Post by zucche on 2007-07-28
i'm on Feisty too and i get "ImportError: No module named pcap" when i start network traffic capture.

i installed pypcap_1.1.deb, dpkt_1.6.deb and packetgarden_1.0.deb from 
[http://selectparks.net/~julian/pg/dists/linux/ubuntu/edgy](http://selectparks.net/~julian/pg/dists/linux/ubuntu/edgy)

i think this is because we are running on Feisty and not on Edgy, but i have no workarounds.

---

### Post by nedrise on 2007-09-13
message from packetgarden website: "News 29-07-07: Packet Garden 1.0 now runs on Ubuntu 7.04 ('Feisty')." -> [http://selectparks.net/~julian/pg/dists/linux/ubuntu/feisty/](http://selectparks.net/~julian/pg/dists/linux/ubuntu/feisty/)

the only problem I encountered was that pg has python2.4 dependencies. if you would like to run it with python2.5 (default on feisty) you have to change line 1 in file pg_garden.py to v2.5.

---

