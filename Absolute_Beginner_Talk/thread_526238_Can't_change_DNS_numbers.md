---
title: "Can't change DNS numbers"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by SanjoEel on 2007-08-15
Ok, I am using Roadrunner for my internet access and basically they suck. I get page load errors and disconnections constantly. I have my suspicions that their network is overcrowded. So, I changed my DNS numbers to those provided by [OpenDNS]("http://www.opendns.com/") and it fixed the problem. Pages load much faster and all is well. That is, until I restart the computer and  my DNS numbers are reset to the crappy RR numbers. I have tried both methods suggested by OpenDNS including editing my /etc/resolv.conf file, and editing the /etc/dhcp3/dhclient.conf file, but neither method works permanently. After a restart everything has changed back. I am awaiting a reply from OpenDNS, but in the meantime, any suggestions?

---

### Post by Hospadar on 2007-08-15
If you remove the "network-manager" and "network-manager-gnome" packages, your network won't get automatically changed anymore.  (this of course also means you won't have any auto configuration, but sounds like you don't want it).  If you still want some auto config for wifi (like if you have a laptop), try getting "wifi-radar" it will scan for wireless networks.


I've never understood why network manager always auto-configs for some people even after you select manual, but meh, you can always just trash it.  It'll stay in your package cache so you can always reinstall them sans connection if you need automatic config.

---

### Post by SanjoEel on 2007-08-15
Thanks I'll give that a shot! I thought it had something to do with the network manager........

---

### Post by SanjoEel on 2007-08-15
Well, I uninstalled the network manager and network manager gnome, but then I could not connect at all. I had to reinstall NM from cache in order to connect Can someone help me configure my network connections without network manager? What info do you need?

---

### Post by zvacet on 2007-08-15
sytem>administration>network > select your modem>select type of conection>close>DNS>put OpenDNS numbers>close


```
pppoeconf
```

Maybe this will help.

---

### Post by SanjoEel on 2007-08-15
Thanks, but that was the first method I tried. The problem is that network manager want to auto configure my DNS settings after each restart, so I have to re-enter my new DNS numbers again. My and my /etc/dhcp3/dhclient.conf file remains as I had altered it, but the settings in Network automatically revert each restart. Here is my /etc/dhcp3/dhclient.conf

> # Configuration file for /sbin/dhclient, which is included in Debian's
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

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 208.67.222.222, 208.67.220.220;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
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
My /etc/resolv.conf reverts to the DNS numbers assigned by Network Manager

---

### Post by stchman on 2007-08-15
> **SanjoEel said:**
> Ok, I am using Roadrunner for my internet access and basically they suck. I get page load errors and disconnections constantly. I have my suspicions that their network is overcrowded. So, I changed my DNS numbers to those provided by [OpenDNS]("http://www.opendns.com/") and it fixed the problem. Pages load much faster and all is well. That is, until I restart the computer and  my DNS numbers are reset to the crappy RR numbers. I have tried both methods suggested by OpenDNS including editing my /etc/resolv.conf file, and editing the /etc/dhcp3/dhclient.conf file, but neither method works permanently. After a restart everything has changed back. I am awaiting a reply from OpenDNS, but in the meantime, any suggestions?

Are you using a router?  if yes then you should put the DNS numbers in the router.

---

### Post by SanjoEel on 2007-08-17
Thanks stchman. I went online to reconfigure my router, and entered the new dns number in the isp box, but I don't think that was right.I can still connect, but the openDNS site says I am not using their numbers Should I switch to static ip instead of dchp and use those numbers as my primary and secondary DNS?

---

### Post by Steve1961 on 2007-08-17
A static IP is always preferable - and if you have a router it's easy to setup.  Just make sure the IP address you give your PC is outside the dhcp address range used by the router

---

### Post by SanjoEel on 2007-08-17
Thanks Steve, but can you clarify that last bit regarding the range? Should  I just use the number assigned by dchp as my IP, and change the DNS numbers manually? Or should I use one of the OpenDNS numbers as my IP? Thanks.

---

### Post by Steve1961 on 2007-08-17
Go into your routers admin page and find the DHCP IP Address Range section.  Mine is set to:

192.168.0.2 to 192.168.0.150

This means I can set an ip address somewhere in the range 192.168.0.151-254.  So I've set mine to 192.168.0.200.  Just set this up in the Ubuntu network dialogue.

If you set an IP within the range (which you can normally change) it will create problems.

You then need to find the sections for the primary and secondary dns servers and enter the opendns numbers there.  make sure the gateway address is set to your routers address (the one you type in the browser to open the admin page)

---

### Post by SanjoEel on 2007-08-17
Thanks a lot man, I'll give this a shot and get back with you!

---

### Post by SanjoEel on 2007-08-20
Well, I am not setting up the static ip configuration right. I can't find a range so I am not sure what to set my IP to. I am still trying to figure out how to permenantly change my DNS numbers if anyone can help.

---

### Post by SanjoEel on 2007-08-20
Ahaaa! Here is the answer. [http://ubuntuforums.org/showthread.php?p=3222872#post3222872]("http://ubuntuforums.org/showthread.php?p=3222872#post3222872")

---

