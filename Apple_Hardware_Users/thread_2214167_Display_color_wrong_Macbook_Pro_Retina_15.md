---
title: "Display color wrong Macbook Pro Retina 15"
date: 2014-03-30
forum: Apple Hardware Users
---

### Post by polo2 on 2014-03-30
I freshly installed ubuntu 12 on my macbook pro 15 retina (2014)
  My display colors are ****ed messed-up, here is a screenshot:

[http://i.stack.imgur.com/1P7Cf.jpg](http://i.stack.imgur.com/1P7Cf.jpg)

Any idea how to fix that ?
  Thanks

---

### Post by mörgæs on 2014-04-04
It's a bad idea to run old software on new hardware. 
As a first step I would suggest 14.04, the almost-finished beta.

---

### Post by polo2 on 2014-04-05
Thank you! Now its work :)

But wifi doesnt, already tried b43 firmware, any idea?

---

### Post by mörgæs on 2014-04-05
Good.
Please run ```
sudo lshw -sanitize -C network > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by polo2 on 2014-04-06
Here is it
```
  *-network UNCLAIMED
       description: Network controller
       product: BCM4360 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:a0600000-a0607fff memory:a0400000-a05fffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=[REMOVED] link=yes multicast=yes
```

---

### Post by mörgæs on 2014-04-06
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by polo2 on 2014-04-06
Much thanks for your help :)
Very good moderator ;P

---

### Post by mörgæs on 2014-04-06
You're welcome. 
Please mark the thread solved using 'thread tools'.

---

