---
title: "Setting up SheepShaver for Networking"
date: 2009-04-08
forum: Apple Hardware Users
---

### Post by afrodeity on 2009-04-08
I am running OS9.04 in emulation using SheepShaver on Ubuntu Hardy 8.04. in the process of setting up networking using this [guide]("http://www.open.ou.nl/hsp/Engels/SheepShaver_Help/networking_2_6.htm")

How does one check is sudo is working on the binaries listed below:

<code>Make sure you have sudo working for your user for the following binaries:

/sbin/ifconfig
/sbin/iptables

Or you will have to run SheepShaver as root.
( on SuSe 9.2 I had to copy one of these files from /usr/sbin to /sbin</code>

How would one fix this? Not sure if it needs fixing, but am stumped right now in the configuration process

---

### Post by cyberdork33 on 2009-04-08
> **afrodeity said:**
> I am running OS9.04 in emulation using SheepShaver on Ubuntu Hardy 8.04. in the process of setting up networking using this [guide]("http://www.open.ou.nl/hsp/Engels/SheepShaver_Help/networking_2_6.htm")

How does one check is sudo is working on the binaries listed below:

<code>Make sure you have sudo working for your user for the following binaries:

/sbin/ifconfig
/sbin/iptables

Or you will have to run SheepShaver as root.
( on SuSe 9.2 I had to copy one of these files from /usr/sbin to /sbin</code>

How would one fix this? Not sure if it needs fixing, but am stumped right now in the configuration process
run 'sudo ifconfig' It should be setup correctly in Ubuntu though.

---

### Post by afrodeity on 2009-04-09
I got the networking running by changing the options from eth0 to slirp, and then selecting DHCP server, manual, in the TCP/IP panel of OS9. Not too bad, if somewhat slow connectivity to the outside world via the router.

---

