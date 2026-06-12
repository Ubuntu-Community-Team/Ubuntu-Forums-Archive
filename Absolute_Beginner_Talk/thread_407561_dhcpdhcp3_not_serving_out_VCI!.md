---
title: "dhcp/dhcp3 not serving out VCI!"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by 13ojo on 2007-04-12
hi,

i have a system using an etherboot floppy, that's setup to obtain ip's via a secondary dhcp server setup on my pc.

i have the /etc/dhcp3/dhcpd.conf looking like

```

not authoritative;
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option vendor-encapsulated-options 3c:09:45:74:68:65:72:62:6f:6f:74:ff;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option root-path "192.168.0.200:/GEEXBOX/";
next-server 192.168.0.200;
filename "/GEEXBOX/boot/pxelinux.0";
shared-network MSHOME {
subnet 192.168.0.0 netmask 255.255.255.0 {
}
}

host Earth {
  hardware ethernet 00:0C:29:84:A4:34;
   fixed-address 192.168.0.203;
   option vendor-encapsulated-options 3c:09:45:74:68:65:72:62:6f:6f:74:ff;
}

host Mars {
  hardware ethernet 04:4b:80:80:03;
  fixed-address 192.168.0.204;
  option vendor-encapsulated-options 3c:09:45:74:68:65:72:62:6f:6f:74:ff;
}



```


when i boot the etherboot floppy with, only use dhcp servers that return "Etherboot" it times out?....

what's wrong with this file?, it doesn't seem to be sending out etherboot. To either PC

---

