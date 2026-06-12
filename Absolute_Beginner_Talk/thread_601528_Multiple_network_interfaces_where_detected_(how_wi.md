---
title: "Multiple network interfaces where detected (how will this work)"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by kentl on 2007-11-03
During installation of Gutsy desktop I got:
```
Multiple network interfaces where detected:
[INDENT]eth0: Intel Corporation PRO/Wireless 2200BG Network Connection (w
eth1: Realtek Semicond
[/INDENT]
```
I choose eth1 to be my primary network interface. It's my LAN port.

What will this result in? If I contact a network address, will it try both network interfaces or just eth1? Will it detect when eth1 isn't connected and use eth0 without a delay?

And how do I switch to eth0 if I need to use my computer through a VLAN.

I prefer to be able to do as much as possible through the command line. But an answer pointing to something in Gnome/KDE might be better than no answer at all. But only might, as I try to use Ratpoison. :)

---

### Post by geforce123 on 2007-11-03
It will uses available interface..

If an interfaces shut, it automagically use the other.

If you want to switch eth0 down, use this command:

```
ifconfig eth0 down
```

---

### Post by myk.dinis on 2007-11-03
Also in ubuntu (gnome flavor) You have a network icon on the taskbar...

choose to manually configure it and then save one configuration with eth0 unchecked as home...
with eth1 checked and configured properly...

And then have another "profile" saved where you have eth1 unchecked and eth0 configured and checked for the vlan...simple as that...

Now...if you want to be sure that eth0 is disconencted try"
sudo ifdown eth0
that's suppoed to bring eth0 down...
and then:
sudo ifup eth0
brings it up

cheers!

Myk

---

### Post by kentl on 2007-11-03
Thanks! I'm not using Gnome so it's not a possiblility for me. But I'll use the ifdown and ifup to bring eth0/1 up and down.

Another question. How do I switch settings for eth0 and eth1?  (Preferably using the command line only.)

This is an example of my needs:

eth1 (cat 5 port)
[LIST=1]
[*]Use DHCP to get IP and DNS-settings at home
[*]Use a static IP and DNS-settings at workplace 1
[*]Use DHCP to get IP but use a static DNS-setting at workplace 2
[/LIST]

eth0: (vlan)
[LIST=1]
[*]Different kind of encryptions and passwords depending on if I'm at home, workplace 1 / 2 or at the local McDonalds.
[/LIST]

---

### Post by geforce123 on 2007-11-10
Well I've never manually started interfaces using dhcp, but here is how to start it with a static ip:

ifconfig eth1 YOUR.IP.HERE YOU.NETMASK.HERE up
you may need to add a default gateway:
route add default gw YOUR.GATEWAY.IP

You can check if the gateway was correctly added:
$ route -n
[.....]
0.0.0.0         198.123.106.161  0.0.0.0         UG    0      0        0 eth1

In this example my gateway is 198.123.106.161

---

