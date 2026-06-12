---
title: "lost internet connection"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by luckydog on 2007-01-23
Help. I've been running Ubuntu for a little over a month after doing the windows thing form 3.11 thru Xp. I can say I love Ubuntu! I am a complete newb really tho. Edgy gets better & faster with every update. My problem is this: I lost my internet connectivty sometime between shutting down sunday night & restarting monday afternoon. Everything worked great prior to that. I'm hard wired to a D-Link router which is also used for my XP machine. After trying a different ethernet card, & different cables with no change, I re-booted using the live CD with reinstallation in mind. I opened Firefox just for grins & had a connection. Why can't I connect when I boot up to the desktop. Please help! I would much rather be using the Ubuntu machine.:confused:

---

### Post by bionnaki on 2007-01-23
post the output of the **network section** of lshw and also post the output of nano /etc/network/interfaces

---

### Post by luckydog on 2007-01-23
-network DISABLED
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@00:04.0
             logical name: eth0
             version: 91
             serial: 00:01:6c:d2:7a:76
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis900 multicast=yes
             resources: ioport:e800-e8ff iomemory:ea022000-ea022fff irq:201

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by bionnaki on 2007-01-23
you need to enable eth0

sudo ifup eth0

---

### Post by luckydog on 2007-01-23
I try to enable etho & get the message:
sudo: must be setuid root
what now?

---

### Post by blitze on 2007-01-23
Funny,
 
I got the same problem with Feisty.  Networking had been fine all through my testing and then beginning of this week, nothing.

Strange.

---

### Post by bionnaki on 2007-01-23
> 
I try to enable etho & get the message:
sudo: must be setuid root
what now?


is that the error? *sudo: must be setuid root*?

can you copy/paste the actual error?

---

### Post by luckydog on 2007-01-24
When I try to run this:

 sudo ifup eth0

 in terminal I get this: 

sudo: must be setuid root

---

