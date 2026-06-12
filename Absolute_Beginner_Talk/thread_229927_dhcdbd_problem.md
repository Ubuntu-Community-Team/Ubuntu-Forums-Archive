---
title: "dhcdbd problem"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by merrameu on 2006-08-05
Hi,

That text apears on my syslog every 30 sec.

---------------
Aug  5 10:44:17 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Aug  5 10:44:17 localhost dhclient: DHCPACK from 192.168.1.1
Aug  5 10:44:17 localhost dhcdbd: dhco_value_from_text: Non ascii char outside valid hex string:  0
Aug  5 10:44:17 localhost dhcdbd: dhco_input_option: Value unit0 cannot be converted to type X
Aug  5 10:44:17 localhost dhcdbd: dhco_parse_option_settings: bad option setting: new_host_name = unit0
Aug  5 10:44:17 localhost dhcdbd: dhco_value_from_text: Non ascii char outside valid hex string:  0
Aug  5 10:44:17 localhost dhcdbd: dhco_input_option: Value unit0 cannot be converted to type X
Aug  5 10:44:17 localhost dhcdbd: dhco_parse_option_settings: bad option setting: old_host_name = unit0
Aug  5 10:44:17 localhost NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0
Aug  5 10:44:17 localhost dhclient: bound to 192.168.1.100 -- renewal in 29 seconds.
-------------

Does anyone know what's that?
I reinstalled dhcdbd but no changes

Any help on this?

Thanks

---

### Post by steve.horsley on 2006-08-05
I woudl guess that the DHCP server on your LAN is dishing out responses that the DHCP client in Ubuntu doesn't like. It also looks like it's trying to allocate the name unit0 to your box.

But it seems that your PC has been allocated an address to use, so I guess you can ignore it. And without any evidence, I would guess that it's the DHCP server and not your box that's not meeting the DHCP protocol spec.

PS
If you didn't know, DHCP is the protocol where a server allocates IP addresses to PCs when they are switched on.

---

### Post by merrameu on 2006-08-06
The olny one problem is that the syslog is very big. The network runs well.
Thanks

---

