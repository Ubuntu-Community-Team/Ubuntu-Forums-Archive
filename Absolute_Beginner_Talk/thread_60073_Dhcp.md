---
title: "Dhcp"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by Radi0ShacK on 2005-08-26
hi all,
i just wanna know how to make my eth0 obtain its ip and dns by using DHCP "i know how to do it using GUI" through Command line "ifconfig eth0 ????? ...etc" Thanks alot.

---

### Post by KingBahamut on 2005-08-26
If memory serves correctly, and someone can poke me if im wrong but. 

ifconfig eth0 dhpc start 

then 

ifconfig eth0 dhcp status

---

### Post by majikstreet on 2005-08-26
[QUOTE=KingBahamut]If memory serves correctly, and someone can poke me if im wrong but. 

ifconfig eth0 dhpc start 

then 

ifconfig eth0 dhcp status[/QUOTE]
 BTW, should be "dhcp" not "dhpc"... LOL!

---

### Post by Radi0ShacK on 2005-08-30
hi, 
sorry for late replay i ve tried #ifconfig eth0 dhcp start and here what i ve got:

> dhcp: Unknown host
ifconfig: `--help' gives usage information. 

so is there any thing should i configure ?? thanks any way

---

### Post by xmastree on 2005-08-30
Try editing /etc/network/interfaces

Mine looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

auto eth0
```

I think you can change this, then use ifconfig down ifconfig up to reset it and load the new data.

**I haven't actually tried this, but this thread had me thinking so I poked around. Use at your own risk or wait for confirmation**

---

### Post by az on 2005-08-30
[QUOTE=Radi0ShacK]hi, 
sorry for late replay i ve tried #ifconfig eth0 dhcp start and here what i ve got:

 

so is there any thing should i configure ?? thanks any way[/QUOTE]
To configure a connection with the GUI is really simple.  Just pick your device and tell it to use DHCP.  If you do not want to use the gui, type

sudo ifdown eth0
sudo dhclient eth0

---

### Post by Radi0ShacK on 2005-08-31
thanks alot every one :)
but azz by doing sudo dhclient eth0, now i can/will obtain ip address and dns ? ex: using my wifi pcmcia card in a public WiFi spot

---

### Post by scrillamaan on 2005-08-31
[QUOTE=Radi0ShacK]thanks alot every one :)
but azz by doing sudo dhclient eth0, now i can/will obtain ip address and dns ? ex: using my wifi pcmcia card in a public WiFi spot[/QUOTE]
I've got the same type of question. At my university I can connect to our free wifi and get and IP address, but no dns. Is there a way to find out through the terminal or something else what the address of the dns server is?

---

