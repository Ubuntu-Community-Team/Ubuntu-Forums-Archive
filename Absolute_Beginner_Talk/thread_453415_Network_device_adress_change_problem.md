---
title: "Network device adress change problem"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by blogmaster on 2007-05-24
hello people, i am having a strange problem. Whenever i run the following command from terminal: 

>  sudo ip link set eth1 address 00:e0:4c:1a:26:06

it first shows me the following error: 

> SIOCSIFHWADDR: Device or resource busy

then after several tries shows the following then:

> sudo: timestamp too far in the future: May 24 05:48:55 2007

i need to change the address of my eth1 but can't do that...i can do the change from Live CD of 7.04 and from rescue mode but not from the actual installation of OS... please help.

---

### Post by Skrynesaver on 2007-05-24
Does eth1 currently have an IP ? 
post the output of 
code]
ifconfig eth1
[/code]

---

### Post by pmg on 2007-05-25
As suggested above, you can't change the MAC address of an active interface (assuming it is active.) You need to shut down the interface first, then your command should work, but it would only have effect until the NIC (Network Interface Card) is reset or powered off.  To make it permanent you have to modify a config file.  I'm new to ubuntu myself, and the config file it uses is different than other flavors of Linux I have used, but it looks like it's controlled by /etc/network/interfaces.  The URL [http://www.debianadmin.com/change-your-network-card-mac-media-access-control-address.html]("http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/") discusses what I think you're trying to do.  Here is another link that discusses a "[macchanger]("http://www.debianadmin.com/change-your-network-card-mac-media-access-control-address.html")" tool that might be helpful.

I haven't done either of these myself on Ubuntu, so can't vouch for how well they work.

---

