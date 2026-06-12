---
title: "The theme changed and the network manager is gone in Debian!"
date: 2011-09-01
forum: Any Other OS
---

### Post by stamatiou on 2011-09-01
Hey guys,
I was surfing on the web in my Debian 6 Laptop and suddenly the network manager icon from the gnome panel vanished and now I can not conndect to the internet! I made a reboot to see if it would be fixed but when i rebooted the default theme was gone and it was replaced by a one callled Custom. I tried to change the theme but Clearlooks is vanished from the Appearance menu too!

Plz help!

---

### Post by garvinrick4 on 2011-09-01
Most likely the applet is just not there.
```
nm-applet
```If does not pop up:
```
sudo /etc/init.d/network-manager restart
```Below wil tell you if anything going on.
```
gedit /var/lib/NetworkManager/NetworkManager.state

```If non of above install.
##Make sure your firmware is installed for network card..
Sometimes have to retrieve from another install and put on flash and install if need cannot get wired or wifi running.
#Below is package network-manager
```
Package: network-manager                 
New: yes
State: installed
Automatically installed: no
Version: 0.9.0-0ubuntu1
Priority: optional
Section: net
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,573 k
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88),
         libglib2.0-0 (>= 2.24.0), libgudev-1.0-0 (>= 147), libnl3 (>= 3.0),
         libnm-glib4 (>= 0.8.9997+git.20110721t045648.36db194), libnm-util2 (>=
         0.9.0), libpolkit-gobject-1-0 (>= 0.99), upstart-job, lsb-base (>=
         3.2-14), wpasupplicant (>= 0.7.3-1), dbus (>= 1.1.2), udev,
         isc-dhcp-client (>= 4.1.1-P1-4), iproute, iputils-arping
Recommends: network-manager-pptp, network-manager-gnome | network-manager-kde |
            plasma-widget-networkmanagement, policykit-1, ppp (>= 2.4.5),
            dnsmasq-base, iptables, modemmanager
Suggests: avahi-autoipd
Conflicts: network-manager
Breaks: network-manager-gnome (< 0.8.99), network-manager-gnome (< 0.8.99),
        network-manager-kde (< 1:0.9~~), network-manager-kde (< 1:0.9~~),
        network-manager-openvpn (< 0.8.99), network-manager-openvpn (< 0.8.99),
        network-manager-pptp (< 0.8.99), network-manager-pptp (< 0.8.99),
        network-manager-vpnc (< 0.8.99), network-manager-vpnc (< 0.8.99), ppp (<
        2.4.5), ppp (< 2.4.5)
Description: network management framework (daemon and userspace tools)
 NetworkManager is a system network service that manages your network devices
 and connections, attempting to keep active network connectivity when available.
 It manages ethernet, WiFi, mobile broadband (WWAN), and PPPoE devices, and
 provides VPN integration with a variety of different VPN services. 
 
 This package provides the userspace daemons and a command line interface to
 interact with NetworkManager. 
 
 Optional dependencies: 
 * policykit-1: Required for reading and writing system connections. 
 * ppp: Required for establishing dial-up connections (e.g. via GSM). 
 * dnsmasq-base/iptables: Required for creating Ad-hoc connections and
   connection sharing. 
 * avahi-autoipd: Used for IPv4LL, a protocol for automatic Link-Local IP
   address configuration.
Homepage: http://www.gnome.org/projects/NetworkManagern


```## Debian you kind of have to know what is going on with drivers to get a clean install, do you ski, it is like the Black Diamonds and not the Bunny slope.
DVD .iso for mint is as close to bunny slope as a debian cousin will get. Can also get .iso in DVD for Ubuntu but Ubuntu now pretty darn user friendly any which way you install. Got Gui app for everything it seems. Will do everything but kiss you good nite anymore.

---

### Post by stamatiou on 2011-09-01
> **garvinrick4 said:**
> Most likely the applet is just not there.
```
nm-applet
```If does not pop up:
```
sudo /etc/init.d/network-manager restart
```Below wil tell you if anything going on.
```
gedit /var/lib/NetworkManager/NetworkManager.state

```If non of above install.
##Make sure your firmware is installed for network card..
Sometimes have to retrieve from another install and put on flash and install if need cannot get wired or wifi running.
#Below is package network-manager
```
Package: network-manager                 
New: yes
State: installed
Automatically installed: no
Version: 0.9.0-0ubuntu1
Priority: optional
Section: net
Maintainer: Ubuntu Core Dev Team <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,573 k
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88),
         libglib2.0-0 (>= 2.24.0), libgudev-1.0-0 (>= 147), libnl3 (>= 3.0),
         libnm-glib4 (>= 0.8.9997+git.20110721t045648.36db194), libnm-util2 (>=
         0.9.0), libpolkit-gobject-1-0 (>= 0.99), upstart-job, lsb-base (>=
         3.2-14), wpasupplicant (>= 0.7.3-1), dbus (>= 1.1.2), udev,
         isc-dhcp-client (>= 4.1.1-P1-4), iproute, iputils-arping
Recommends: network-manager-pptp, network-manager-gnome | network-manager-kde |
            plasma-widget-networkmanagement, policykit-1, ppp (>= 2.4.5),
            dnsmasq-base, iptables, modemmanager
Suggests: avahi-autoipd
Conflicts: network-manager
Breaks: network-manager-gnome (< 0.8.99), network-manager-gnome (< 0.8.99),
        network-manager-kde (< 1:0.9~~), network-manager-kde (< 1:0.9~~),
        network-manager-openvpn (< 0.8.99), network-manager-openvpn (< 0.8.99),
        network-manager-pptp (< 0.8.99), network-manager-pptp (< 0.8.99),
        network-manager-vpnc (< 0.8.99), network-manager-vpnc (< 0.8.99), ppp (<
        2.4.5), ppp (< 2.4.5)
Description: network management framework (daemon and userspace tools)
 NetworkManager is a system network service that manages your network devices
 and connections, attempting to keep active network connectivity when available.
 It manages ethernet, WiFi, mobile broadband (WWAN), and PPPoE devices, and
 provides VPN integration with a variety of different VPN services. 
 
 This package provides the userspace daemons and a command line interface to
 interact with NetworkManager. 
 
 Optional dependencies: 
 * policykit-1: Required for reading and writing system connections. 
 * ppp: Required for establishing dial-up connections (e.g. via GSM). 
 * dnsmasq-base/iptables: Required for creating Ad-hoc connections and
   connection sharing. 
 * avahi-autoipd: Used for IPv4LL, a protocol for automatic Link-Local IP
   address configuration.
Homepage: http://www.gnome.org/projects/NetworkManagern


```## Debian you kind of have to know what is going on with drivers to get a clean install, do you ski, it is like the Black Diamonds and not the Bunny slope.
DVD .iso for mint is as close to bunny slope as a debian cousin will get. Can also get .iso in DVD for Ubuntu but Ubuntu now pretty darn user friendly any which way you install. Got Gui app for everything it seems. Will do everything but kiss you good nite anymore.

Thaank you very much for answering but I installed it again :P

---

### Post by NightwishFan on 2011-09-01
The only way this would happen is if a bunch of needed packages got removed. Hope you got it sorted out. If you want to make sure the full gnome desktop is installed just run (as root)
```
tasksel install gnome-desktop
```

---

