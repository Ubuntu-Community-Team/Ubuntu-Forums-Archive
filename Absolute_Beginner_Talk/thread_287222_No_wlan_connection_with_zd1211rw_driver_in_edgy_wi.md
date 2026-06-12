---
title: "No wlan connection with zd1211rw driver in edgy with 2.6.17 kernel"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by fanpan on 2006-10-28
I am using a Sitecom WL113 Wireless USB Dongle with a zd1211 chipset to connect to internet. In Ubuntu 6.06 this works just fine. However, since upgrading to 6.10, I get no connection.

When I boot 6.10, but specify in GRUB to use the 2.6.15-27-686 kernel, I can get a connection. However, with the 2.6.17-10-386 kernel, no joy. This probably has to do with the zd1211rw driver in the newer kernel as opposed to the zd1211 driver in the older kernel.

Looking in the system log under messages, I find:

kernel: [17179602.584000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
kernel: [17179602.584000] IPv6 over IPv4 tunneling driver

I then tried the following:
modprobe -v zd1211rw
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid XXXXXX

The system log message then becomes:
kernel: [17180221.860000] SoftMAC: Open Authentication completed with 00:XX:XX:XX:XX:XX
kernel: [17180221.880000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

However there is still no connection

In the syslog I find the following:
dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
dhclient: No DHCPOFFERS received.
dhclient: Trying recorded lease 10.0.0.13
avahi-daemon[4562]: New relevant interface wlan0.IPv4 for mDNS.
avahi-daemon[4562]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.13.
avahi-daemon[4562]: Registering new address record for 10.0.0.13 on wlan0.
avahi-daemon[4562]: Withdrawing address record for 10.0.0.13 on wlan0.
avahi-daemon[4562]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.13.
avahi-daemon[4562]: iface.c: interface_mdns_mcast_join() called but no local address available.
avahi-daemon[4562]: Interface wlan0.IPv4 no longer relevant for mDNS.
avahi-daemon[4562]: New relevant interface wlan0.IPv4 for mDNS.
avahi-daemon[4562]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.13.
avahi-daemon[4562]: Registering new address record for 10.0.0.13 on wlan0.
dhclient: No working leases in persistent database - sleeping.
avahi-daemon[4562]: Withdrawing address record for 10.0.0.13 on wlan0.
avahi-daemon[4562]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.13.
avahi-daemon[4562]: iface.c: interface_mdns_mcast_join() called but no local address available.
avahi-daemon[4562]: Interface wlan0.IPv4 no longer relevant for mDNS.

Also, there is line which says no IPv6 routers present.

As an absolute beginner, this is all chinese to me.:(  Ideas, Anybody?

---

### Post by Bachstelze on 2006-10-28
Configure your interface using a GUI app, network-admin in GNOME or the KDE Wireless Assistant.

---

