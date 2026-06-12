---
title: "ipconfig"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by CanonD on 2006-09-20
is there an ipconfig sort of thing in linux?

i my nic died and was only able to figurethings out in windows.

ipconfig /all
/release
/renew

are the ones i use the most.

---

### Post by Iowan on 2006-09-20
**ifconfig**?
I was amazed at all the things **ifconfig** can do after reading **man ifconfig**.

---

### Post by Omnios on 2006-09-20
Hi Ubuntu has ifconfig as a ip config and release.

 ```

sudo ifconfig eth0 down
sudo ifconfig eth0 up\
sud dhclient eth0

```terminal help entry
```

tom@miko:~$ ifconfig --help
Usage:
  ifconfig [-a] [-v] [-s] <interface> [[<AF>] <address>]
  [add <address>[/<prefixlen>]]
  [del <address>[/<prefixlen>]]
  [[-]broadcast [<address>]]  [[-]pointopoint [<address>]]
  [netmask <address>]  [dstaddr <address>]  [tunnel <address>]
  [outfill <NN>] [keepalive <NN>]
  [hw <HW> <address>]  [metric <NN>]  [mtu <NN>]
  [[-]trailers]  [[-]arp]  [[-]allmulti]
  [multicast]  [[-]promisc]
  [mem_start <NN>]  [io_addr <NN>]  [irq <NN>]  [media <type>]
  [txqueuelen <NN>]
  [[-]dynamic]
  [up|down] ...

  <HW>=Hardware Type.
  List of possible hardware types:
    loop (Local Loopback) slip (Serial Line IP) cslip (VJ Serial Line IP)
    slip6 (6-bit Serial Line IP) cslip6 (VJ 6-bit Serial Line IP) adaptive (Adaptive Serial Line IP)
    strip (Metricom Starmode IP) ash (Ash) ether (Ethernet)
    tr (16/4 Mbps Token Ring) tr (16/4 Mbps Token Ring (New)) ax25 (AMPR AX.25)
    netrom (AMPR NET/ROM) rose (AMPR ROSE) tunnel (IPIP Tunnel)
    ppp (Point-to-Point Protocol) hdlc ((Cisco)-HDLC) lapb (LAPB)
    arcnet (ARCnet) dlci (Frame Relay DLCI) frad (Frame Relay Access Device)
    sit (IPv6-in-IPv4) fddi (Fiber Distributed Data Interface) hippi (HIPPI)
    irda (IrLAP) ec (Econet) x25 (generic X.25)
    eui64 (Generic EUI-64)
  <AF>=Address family. Default: inet
  List of possible address families:
    unix (UNIX Domain) inet (DARPA Internet) inet6 (IPv6)
    ax25 (AMPR AX.25) netrom (AMPR NET/ROM) rose (AMPR ROSE)
    ipx (Novell IPX) ddp (Appletalk DDP) ec (Econet)
    ash (Ash) x25 (CCITT X.25)


```also check dhclient --help

 Note: oh ya my network is eth0 you might have something different

---

### Post by ignorance on 2006-09-20
> **Omnios said:**
> 
 Note: oh ya my network is eth0 you might have something different

Usually Ubuntu names the first networkcart eth0, the second one eth1, and so on. If i remeber correctly.

So i think his one will be named eth0 also duno how it works with wireless.

---

### Post by CanonD on 2006-09-20
thanks a bunch :-d

i guess mine will be eth1 since my eth0 is dead :(

---

### Post by Omnios on 2006-09-20
> **CanonD said:**
> thanks a bunch :-d

i guess mine will be eth1 since my eth0 is dead :(

If I remember properly there is also ppo for dsl but that might have been dial up lol.

---

### Post by Dragon43 on 2007-02-04
I just found that I could use this to find the IP the router assigned to this computer and so I couold then put that IP into ZoneAlarm so that this Ubuntu computer could see into one of the two 
win-98se boxes I have on my inhouse network.

ZoneAlarm 5.5

The other Win 98se box has ZoneAlarm 4.5 and it does not block the inhouse network at all.

I had the Laptop with XP home working with the 98se computers, so I need to try to get the Ubuntu computer to see into it for file transfers.

I have given up for now trying to get the Win Boxes to see into the Ubuntu 6.06 Box,  Seems toi be a real problem and I have too much other stuff to learn now.  I only have been messing with this for 8 days and I am so ignorant that I don't even know what questions to ask.

My 'Search Fu' sucks rocks. I need a simpler way to find stuff.

---

### Post by Dragon43 on 2007-02-04
> **Dragon43 said:**
> I just found that I could use this to find the IP the router assigned to this computer and so I couold then put that IP into ZoneAlarm so that this Ubuntu computer could see into one of the two 
win-98se boxes I have on my inhouse network.

ZoneAlarm 5.5

The other Win 98se box has ZoneAlarm 4.5 and it does not block the inhouse network at all.

I had the Laptop with XP home working with the 98se computers, so I need to try to get the Ubuntu computer to see into it for file transfers.

I have given up for now trying to get the Win Boxes to see into the Ubuntu 6.06 Box,  Seems toi be a real problem and I have too much other stuff to learn now.  I only have been messing with this for 8 days and I am so ignorant that I don't even know what questions to ask.

My 'Search Fu' sucks rocks. I need a simpler way to find stuff.

Got it done, with or without ZoneAlarm running:
This post comes from an Ubuntu computer that can see and transfer files from all the computers on it's 'inhouse' network.
1 HP laptop, OS = XP home
2 home made PC's, OS = Win 98se
1 Emachine, OS = Ubuntu 6.06 linux

*::: Whew :::: * :)  :)  :)  :)  :)  :)

---

