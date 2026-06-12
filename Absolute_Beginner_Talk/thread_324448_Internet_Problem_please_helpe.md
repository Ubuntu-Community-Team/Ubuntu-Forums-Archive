---
title: "Internet Problem please helpe"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-12-23
I dont know why my connection is not solid since i strated using edgy last month and even with several fresh install.
My connection to internet only last for 2 minutes, then i have to type in "sudo dhclient".
I dont even know what the command does except that it get me connected for another 2 minutes.
i realy need some help cause i cant stand that anymore](*,) 
thanks

---

### Post by taurus on 2006-12-23
Is that a wireless or ethernet connection?

---

### Post by kiyometane on 2006-12-23
ethernet connection

---

### Post by mendingo84 on 2006-12-23
what kind of connection do u have? is it a LAN? is it ppp? is it pppoe...

---

### Post by kiyometane on 2006-12-23
it is a lan connection.
the router is connected to a broadband modem. And i have a dynamic ip address

---

### Post by mendingo84 on 2006-12-23
read the output of this carefully:
> 
man dhclient
you could also post the output of dhclient.conf . maybe you missconfigured your dhcp server and the IP' s TTL for a host is set to 2 minutes. check that as well.

---

### Post by kiyometane on 2006-12-23
this is the dhclient.conf

# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

---

### Post by mendingo84 on 2006-12-23
ok...check your DHCP server. there must be a time to live (TTL) setting. this means for how long should your host posses an IP. maybe that TTL is set to 2 minutes... what dhclient does is to request a new IP, subnet mask and all those things.

---

### Post by kiyometane on 2006-12-23
how do i check my dhcp server?

---

### Post by mendingo84 on 2006-12-23
oh!...so you have only one host connected through the router? in that case, there's nothing for you to check as the DHCP server is owned by your ISP and you don't have access to it. if that is so, it is strange why your connection holds, it shouldn't. this won't solve your problem, but, next time it happens, check if you have an IP: type "ifconfig". next, try to restart your interface :"sudo /etc/init.d/networking restart".
if you are on a small LAN, one of the hosts might be used as the DHCP server. that means it is running a specific application. that's where you should check, in the configuration file of that specific application on that specific host...
i hope i was helpful although i didn't solve your problem...

---

### Post by mendingo84 on 2006-12-23
oh, also, check your router configuration. open a browser and type 192.168.1.1
find the refferal to DHCP (if it exists) and check what's in there...

---

### Post by kiyometane on 2006-12-23
i forgot to mention, i have pc connected to a router which make it 2 host

---

### Post by kiyometane on 2006-12-23
> **mendingo84 said:**
> oh, also, check your router configuration. open a browser and type 192.168.1.1
find the refferal to DHCP (if it exists) and check what's in there...
dhcp server enabled
client lease time 0 minutes (0 means 1 day)

just the basick interface of a linksys router

---

### Post by kiyometane on 2006-12-23
I'm not sure if the cause was that my computer time was set an hour in advance, so a confusion was created in the lease files in long run.
i deleted all dhclient.ehtx.leases and dhclient.leases in var/lib/dhcp3 folder and rebooted
the internet is working for the time being and if it lasted for days, the wrong timing may the reason
i would go bersek i were to lose connection again

---

### Post by mendingo84 on 2006-12-24
glad you found out what the problem was

---

