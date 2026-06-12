---
title: "Upgrade left me unable to connect to internet"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-07-28
I finally broke down and did the upgrade to Dapper...
Well, it happened! lol
I took the box up and connected it to router via cat-5, and get nothing... Checked the settings on the router, and my info is right. Wireless doesn't work either... No connectivity to router, even when wired... any ideas?
It's a Dell Lattitude C-600
I have the bcm43xx card, and iwconfig(?) shows it has drivers loaded...

---

### Post by Papa-san on 2006-07-28
LOL... I cannot ping my router via wired connection!?!:confused:

---

### Post by ProjectGod on 2006-07-28
make sure you've "activated" the network adapter from the "networking" GUI tool. and if that is true... try pinging the loopback 127.0.0.1

if that both works. check router to see if it's DHCP enabled. if its dishing out IPs then make the ubuntu a DHCP client also.

let us know how you go.

---

### Post by Papa-san on 2006-07-28
> **ProjectGod said:**
> make sure you've "activated" the network adapter from the "networking" GUI tool. and if that is true... try pinging the loopback 127.0.0.1

if that both works. check router to see if it's DHCP enabled. if its dishing out IPs then make the ubuntu a DHCP client also.

let us know how you go.

Yup... activated eth0
(removed wlan0 until I get this thing hooked up to the router)
Pinged loopback ok...
Router is dhcp enabled and ubuntu is dhcp as well...

---

### Post by ProjectGod on 2006-07-28
you've probably done this... but can you ping your router's IP rather than its name? 

check that the link lights are blinking and that the collision lights are't continuously on.

furthermore can you give us the output for 

/etc/network/interfaces

---

### Post by Papa-san on 2006-07-28
Yeah, I've tried the  ip... No response. (I haven't tried the name?)

/etc/network/interfaces: 
auto: eth)

wlan0 primary, it shows the proper ip (192.168.2.103), subnet, essid, wep, and gateway... but this isn't showing up in 'networking'

eth0 not active, all there as well as wan id, and wep key.(192.168.2.103)

eth1 active, shows ip is static. (192.168.2.135) (?)
subnet and gateway are right...

---

### Post by ProjectGod on 2006-07-28
eth0 not active?
eth1 active? how many network adapters do you have?

in the networking GUI tool. make sure the default gateway is eth0 (the one that has cat 5 plugged in) and not wireless etc

oops! i know this is a pain but could you also grab for us more info concerning network config...

at the command prompt:

ifconfig

dont worry about the HWaddr ir Inet6 addr or other settings that deal with collisions and errors.

hmmmm wlan0 is primary... that could be the issue. if its not showing in the GUI networking utility... you may have to directly edit it via the conf file so that eth0 becomes your primary address... 

i've never experienced this with ubuntu but some say if you have IP v6 enabled internet doesnt work. perhaps you could search these forums for IP v6 problems.

cheers.

---

### Post by ProjectGod on 2006-07-28
ahh. ok. this may help. i've personally got a static IP setup. but in your:

/etc/network/interfaces... your settings must read

[B]# the  primary network interface must be:
iface eth0 inet dhcp

auto eth0[/B]

i've personally got

# the primary network interface
iface eth0 inet static
address 192.168.200.4
netmask 255.255.255.0
network 192.168.200.0
broadcast 192.168.200.255
gateway 192.168.200.1

please make a copy of this file before fiddling with it using cp.

i'm assuming eth0 is the ethernet card that's connecting to the router... the above may or maynot work... but i'm 100% sure if you tweak this file correctly you'll get to ping the router... using your ethernet rather than wireless... right now i think ubuntu is being mixed up (somehow) with which interface to use and which one should be primary. 

you may be best off if you just ask someone who has a basic DHCP enabled ethernet / internet connection to give their /etc/network/interfaces settings... and just duplicate it on your system changing where necessary.

let us know how you go...

---

### Post by confused57 on 2006-07-29
Here's my output of /etc/network/interfaces:

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

# The primary network interface
iface eth0 inet dhcp

This on my computer(D-Link PCI network card) running Breezy, which I guess I'll have to upgrade by April 2007 when it's no longer supported.  The Dapper Live CD works fine on this machine, so hope that's a good indication.  Not that it would have made any difference, but which method did you use to upgrade: manually by editing sources.list, CD Rom, or click on the Update Manager "upgrade" button?

I have another computer running Dapper, I'll check it later & see if there is any difference, wouldn't think so.  Checked...Here's my Dapper(integrated network controller) entry:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by Papa-san on 2006-07-29
(There are other files in /etc/network, named:
'interfaces.dpkg.old' , and 'options.dpkg-bak')???

Here is the info from /etc/network/interfaces:
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

auto eth0


# The primary network interface
iface wlan0 inet static
wireless-essid ubuntu
wireless-key (correct)
address 192.168.2.103
netmask 255.255.255.0
gateway 192.168.2.2

iface eth1 inet static
address 192.168.2.135
netmask 255.255.255.0
gateway 192.168.2.2
wireless-essid ubuntu
wireless-key s:(correct)

iface eth0 inet static
address 192.168.2.135
netmask 255.255.255.0
gateway 192.168.2.2

Upgrade via 'button'in (?) interface...

---

### Post by confused57 on 2006-07-29
There's some guides here to troubleshooting network issues:

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

This section of the above link may help:

[http://doc.gwos.org/index.php/NetworkMagicBreezy](http://doc.gwos.org/index.php/NetworkMagicBreezy)

---

### Post by Papa-san on 2006-07-29
here's my ifconfig:
```
john@ubuntu:~$ ifconfig
eth0      
Link encap:Ethernet  HWaddr 00:06:5B:E1:BA:40
inet addr:192.168.2.135  Bcast:192.168.2.255  Mask:255.255.255.0
inet6 addr: fe80::206:5bff:fee1:ba40/64 Scope:Link

UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

RX packets:32258 errors:0 dropped:0 overruns:0 frame:0
TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000
RX bytes:2170622 (2.0 MiB)  TX bytes:3604 (3.5 KiB)
Interrupt:11 Base address:0xec00

lo

Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:603946 errors:0 dropped:0 overruns:0 frame:0
TX packets:603946 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:0
RX bytes:150120892 (143.1 MiB)  TX bytes:150120892 (143.1 MiB)

john@ubuntu:~$
```

Also contents of 'interfaces.dpkg-old:
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

# The primary network interface
iface wlan0 inet dhcp
wireless-essid ubuntu
wireless-key ( correct) 

auto wlan0

I'll check that link, thanks!

---

### Post by Papa-san on 2006-07-29
I tried to ping my router, and I get:
operation not permitted... over and over again

---

