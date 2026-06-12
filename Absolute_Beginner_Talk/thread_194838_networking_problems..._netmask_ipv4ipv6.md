---
title: "networking problems... netmask? ipv4/ipv6?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by black bear theory on 2006-06-12
i just did a LAMP server 6.06 on an old PIII i have for a little bit. the installation went fine, but my internet doesn't work. i've searched the the forums and have decided that the subnetmask of my router (255.255.255.0) and my computer (255.255.255.255) are not the same.

however, i don't know how to change it. i tried uncommenting the "option subnet-mask 255.255.255.0" in dhclient.conf to no avail.

also, when i try to ping my router, mac, or gentoo box it says "connect: Network is unreachable"  probably because of the subnetmask thing.

any ideas?

---

### Post by black bear theory on 2006-06-12
i have internet working. i can ping and traceroute just fine now.

though i can't 'apt-get update'. *those* ftp connections don't work for some reason. i did catch an ftp connection *once*, but it stopped after a few minutes.

---

### Post by jvictor on 2006-06-12
The best solution I guess here is to use a static IP.

Usually if u r using a adsl router it's IP will be 192.168.1.1
and ur machine will have 192.168.1.2

Another reason can be IPV6 is messing up ur net conxn
Disable IPv6 on ur machine

At last use the ISPs DNS server instead of ur Router in /etc/resolv.conf

If none of this work give us the following info

Ur IP
Ur Routers IP

and the output of these commands

ifconfig -a
route -n
less /etc/hosts
less /etc/resolv.conf
less /etc/modprobe.d/aliases

---

### Post by black bear theory on 2006-06-13
thanks for the reply, jvictor. i got everything working last night and was too tired to close off the thread.

anyway, this is what i did (culled from info on these forums) for posteriety.


**1. my network adaptor** wasn't working with the tulip driver so i had to switch it to the dfme driver. now i could access *a* network, though, i'm not sure which one it was.


**2. i added the line** "netmask 255.255.255.0" to my /etc/network/interfaces file
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
**netmask 255.255.255.0**
```
after this step, i could access the network through 'ping' and 'traceroute' but oddly not via apt-get.


**3. changed my /etc/apt/sources.list** file as such:
```
#
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


#deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb ftp://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src ftp://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb ftp://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src ftp://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```
basically i changed it from ftp access to http (replace all 'ftp' with 'http') and all references to 'us.archive.ubuntu.com' to 'archive.ubuntu.com'.

now i had the internet and apt-get working! phew!

**other ideas i tried:** disabling ipv6 but that didn't work to get my internet up.

i'm not sure if it's me, but the default files for installation seemed to need a lot of tuning for things to work. i am on older hardware though.

bbt

p.s. how do i put SOLVED into the thread title

---

