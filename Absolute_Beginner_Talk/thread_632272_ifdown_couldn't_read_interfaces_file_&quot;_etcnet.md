---
title: "ifdown: couldn't read interfaces file &quot; /etc/network/interfaces&quot;"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by fullmesh on 2007-12-05
Hi EVERYONE

I have gone through all simillar posts, but non help so far.

My problem started when i tried to change dhcp to inet static using "sudo vi /etc/network /interfaces"

being a newbie with the command in VIM. at first the cursor stucked and i couldn't type a thing not knowing the syntax. anyway i was some how able to make the change and couldn't save the changes I made I've to reboot the server using the start button. there after the network could not come up.
I use nano since i'm more famillier with it it come up with the following:

# This file describes the network interfaces available on your system
and how to activate them. For more information, see interfaces(5).

#>  The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.172.242
netmask 255.255.255.0
network 192.168.172.0
broadcast 192.168.172.255
gateway 192.168.172.1


After I restart the network

[PHP]sudo /etc/init.d/networking restart[/PHP]


I got the following error msg



* Reconfiguring network interfaces......
/etc/network/interfaces:2: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:2: misplace option
ifup: couldn't read interfaces file "/etc/network/interfaces"

[fail]


PLEASE COULD anyone help bring up this net i'm trying to setup a LAMP server

THANKS

Tanimu
[email]tambalzar@gmail.com[/email]

---

### Post by bodhi.zazen on 2007-12-06
Thread moved to a more appropriate location.

---

