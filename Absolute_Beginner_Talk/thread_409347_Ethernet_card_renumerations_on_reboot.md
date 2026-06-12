---
title: "Ethernet card renumerations on reboot"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Pontiac on 2007-04-14
Please keep in mind, no physical changes have been done to the machine on a hardware level.

I've just recently upgraded my store network to work on GigE.  In my linux box, I have two ethernet cards, one on board, one as a PCI working the new GigE.  Both NICs are hooked up to seperate networks entirely.  The GigE card is on a 10.x.x.x network, the onboard is working on a 192.168.x.x network.

Just recently, unknown why, the machine decided to reboot spontaneously.  I was in the middle of watching a flick on YouTube on another machine when everything went down.  I went to the linux box since its my DHCP3 server.  Prior to the reboot EVERYTHING was working absolutly beautifully.  Yesterday, I was restarting the DHCP server on a constant basis while I ensured that changes made to the dhcp.conf file were applied to the particular machine I was working with.

When I noticed the network was down, I checked the linux box, and it had been rebooted somehow.  I don't know why, I don't care why.  I logged in, started up two consoles.  One to restart the service, the other to tail log files.

When in the service console, it told me that it failed to shut down the service (Expected), but it also told me it failed to start the service (Unexpected).  Checked the log console, and messages showed me that it looked like everything was just fine.  It told me it wrote two licenses.  Unhappy with messages, I checked syslog and IT told me that the service wasn't configured to listen to any ethernet cards.  I'm like WTF? (Fudge)

So I checked the config file (/etc/default/dhcp3.conf) and it was set to eth2.  Which is where its been all along.

I changed it to eth1, saved, then restarted the service, and voila, I'm here.

This isn't the first time I've noticed that particular cards enumeration getting swapped around.  Its really critical that the enumeration STAYS at either eth1 or eth2.  I don't care which, but I do care to know why it thinks its funny to move that numeration.

Any help to force ubuntu to KEEP that ethernet enumeration in place would be greatly appreciated.

---

### Post by chalex on 2007-04-14
What does "dmesg|grep eth" tell you?  What does your /etc/network/interfaces look like?  Take a look at the mapping option in "man interfaces".

---

### Post by Pontiac on 2007-04-14
```

root@radius:~# dmesg | grep eth
[17179595.616000] eth0: VIA Rhine II at 0x1a000, 00:0c:6e:74:fb:00, IRQ 177.
[17179595.616000] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[17179596.152000] eth1: Identified chip type is 'RTL8169s/8110s'.
[17179596.152000] eth1: RTL8169 at 0xe0898000, 00:18:e7:08:bc:7a, IRQ 185
[17179598.528000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179598.592000] r8169: eth1: link down
[17179598.976000] r8169: eth1: link up
[17179610.304000] eth1: no IPv6 routers present
[17179610.640000] eth0: no IPv6 routers present

```

```

root@radius:~# cat /etc/network/interfaces
auto lo eth1 eth0
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet static
        address 192.168.1.254
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0

iface eth1 inet static
        address 10.1.1.254
        netmask 255.255.255.0
        broadcast 10.1.1.255
        network 10.1.1.0
        gateway 10.1.1.1





iface eth2 inet static
address 10.1.1.254
netmask 255.255.255.0
gateway 10.1.1.1

auto eth2

```

The only thing of recent I did change was adding a gateway eth2 because I couldn't get this machine out to the net.  Once I did that, the net was working fine.  The machine was working on eth2.  But due to the reboot, it decided to go back to eth1.

---

### Post by Pontiac on 2007-04-14
From man interfaces.

```

KNOWN BUGS/LIMITATIONS
       The ifup and ifdown programs work with so-called "physical" interface names.  These names are assigned to hardware by the kernel.  Unfortunately it
       can  happen that the kernel assigns different physical interface names to the same hardware at different times; for example, what was called "eth0"
       last time you booted is now called "eth1" and vice versa.  This creates a problem if you want to configure the interfaces appropriately.  A way  to
       deal  with  this  problem is to use mapping scripts that choose logical interface names according to the properties of the interface hardware.  See
       the get-mac-address.sh script in the examples directory for an example of such a mapping script.  See also Debian bug #101728.

```

Thats bogus.  I'll have to look into that script later. *shakes his head*

---

