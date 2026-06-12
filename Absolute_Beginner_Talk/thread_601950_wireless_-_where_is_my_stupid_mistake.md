---
title: "wireless - where is my stupid mistake"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-11-03
I got a wmp11 to work on gutsy on my other computer.  Just did a fresh install on another computer and up that one to gutsy as well.  I can not seem to get the card to work on one of the machines:  Here are some out puts, any help would be nice thanks

@carputer:~$ sudo ndiswrapper -l
[sudo] password for endlessurf:
lsipnds : driver installed
        device (17FE:2120) present

@carputer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


@carputer:~$ sudo lshw
.........
    *-network:0 **UNCLAIMED**
                description: Ethernet controller
                product: WMP11v4 802.11b PCI card
                vendor: Linksys, A Division of Cisco Systems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=32 mingnt=32
.......

Any ideas thanks

---

### Post by skymera on 2007-11-03
can tyou give more details on your carD?

usb? pci?
make/model?

---

### Post by endlessurf on 2007-11-03
product: WMP11v4 802.11b PCI card

---

### Post by skymera on 2007-11-03
how have you got your network setup?

automatic or manual?

i always prefer manual, 

sudo network-admin

go to wireless and see if any networks appear in drop down box, if so, your card is working.

sorry im not much help, im not a master at networking :(

---

### Post by endlessurf on 2007-11-03
that is where i am stupped at, when i go to manual, there is no wireless settings option

---

### Post by skymera on 2007-11-03
=|

ok thats strange, what version of ubuntu have you got?

where did you download?

---

### Post by endlessurf on 2007-11-03
I had a 64 fiesty and then upped it to gutsy using the update manager

if you look in my original post there is a spot where it says network unclaimed,  I think that might be where the problem is,  but i am most likely wrong

---

### Post by skymera on 2007-11-03
ok i suggest a straight fresh download and frsh install
here my netrwork thing:

```

             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Wireless interface
                product: RT2561/RT61 802.11g PCI
                vendor: RaLink
                physical id: 3
                bus info: pci@0000:03:03.0
                logical name: wmaster0
                version: 00
                serial: 00:17:3f:28:e5:ce
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless

```

32bit is also more supproted :wink:

also when i made a custom kernel it didnt have a wireless box, so maybe somethings missing from yours?

anyway try a new install, and see if its fine.
if not, we see from there.

godd luck

---

### Post by endlessurf on 2007-11-03
the one problem with the fresh install is i have already done it multiple times and I spent many hours configuring my  touchscreen.  I would hope someone in the community would know enough to say: just do this, or your problem is way over your head and it would take me to much time.  I just don't give up that easily

---

### Post by endlessurf on 2007-11-03
here is some more info lspci -v


01:00.0 Ethernet controller: Linksys, A Division of Cisco Systems WMP11v4 802.11b PCI card
        Subsystem: Linksys Unknown device 0020
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at f1001000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

---

### Post by skymera on 2007-11-03
o, i wansnt sure if you tried reinstalling,

sorry :( ive run out of knowledge

hope someone else can help you

---

### Post by endlessurf on 2007-11-21
so i have reinstalled again.....   this time  32 bit gutsy and started with a fresh download.  any ideas????????????//

---

