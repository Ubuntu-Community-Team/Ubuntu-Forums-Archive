---
title: "Internet via LAN cable"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by siroche on 2008-02-25
Hi, just converted an older laptop to Ubuntu. I'm a new user. Running 7.1
I cannot get my internet connection to work. I use a D-Link broadband router and have plugged in a network cable to it but cannot get a page to show up. It seems to ping ok though from the laptop. (System > Administrator > Network Tools).  When I use my work laptop it automatically connects OK. 

Need some help here guys.
Settings Are (system > Administration > Network)
Wired Connection > Properties = Roaming enabled (tried connection settings - no joy either
DNS looks to be pointing at the D-LINK address
Don;t know what the HOSTS stuff is all about

Also, how do I find out if my machine still has a wireless connector?

---

### Post by thisiam on 2008-02-25
does your laptop connect when you bypass the router? do you have static or dynamic IP set?
is your router set to DHCP or manually set ?
what model of laptop do you have? older laptops don't necessarily come with built in wireless
and Linux is not to wireless friendly. if you do have wireless remember to Google this later on
ndiswrapper

---

### Post by HereInOz on 2008-02-25
D-Link router/modems are notorious for not passing DNS information correctly to a Linux machine.

This is what you need to do:

First up find out the IP addresses of your ISP's DNS servers - you will need them later on.

Then go to System > Administration > Network and find your active network connection. Click on Properties and then:

1. Disable roaming mode
2. Select the option of Static IP address
3. Enter an IP address for your computer which is in the same subnet as your gateway IP (keep the first 3 sets of 3 numbers the same)  For example, if your D-Link is set at the default settings, your gateway address will probably be 10.1.1.1.  Set the address of your computer to, say, 10.1.1.2.
4. Enter the IP address of your gateway in the appropriate field.
5. Click OK

Then in the network dialog box, click on the DNS tab, and enter the address(es) of your ISP's DNS servers and then click close.

You then need to restart your network interface, or just restart the machine.

See if that helps your cause.

---

### Post by louieb on 2008-02-25
For a wired connection roaming or not both work on mine.
Having the router IP for your DNS Server is normal too.

Try two things Open applications>accessories>terminal
list your network connections
```
ifconfig
```
and try to get an IP address via dhcp
```
sudo dhclient
```
if it doesn't work  check the connection make sure its good and tight.
Also if you could post the output of the two commands above it would help.

---

### Post by siroche on 2008-02-26
> **HereInOz said:**
> D-Link router/modems are notorious for not passing DNS information correctly to a Linux machine.

This is what you need to do:

First up find out the IP addresses of your ISP's DNS servers - you will need them later on.

Then go to System > Administration > Network and find your active network connection. Click on Properties and then:

1. Disable roaming mode
2. Select the option of Static IP address
3. Enter an IP address for your computer which is in the same subnet as your gateway IP (keep the first 3 sets of 3 numbers the same)  For example, if your D-Link is set at the default settings, your gateway address will probably be 10.1.1.1.  Set the address of your computer to, say, 10.1.1.2.
4. Enter the IP address of your gateway in the appropriate field.
5. Click OK

Then in the network dialog box, click on the DNS tab, and enter the address(es) of your ISP's DNS servers and then click close.

You then need to restart your network interface, or just restart the machine.

See if that helps your cause.

Tried all of that - no good. Rebooted too. Under the properties bit I was not sure what to set the Subnet Mask to. It defaulted to 255.0.0.0. I'm not sure what you mean by the Gateway Address - is this something I get form the D-ling router? Anyway, as you can tell I'm really not that sure what I'm meant to be doing ! PS I also did the DNS bit - added in the two IP addresses for the ISP
So current settings are:
In the properties box:
Static IP address option set
IP address 10.1.1.5
subnet 255.0.0.0
Gateway address = ISP address (is that correct?)

DNS = gateway = ISP IP addresses (2)

---

### Post by oedha on 2008-02-26
gateway = your router ip
dns = your ISP 's dns server number

---

### Post by siroche on 2008-02-26
OK. thats alot of message stuff to type in since I can't paste 
HWaddr 00.08.02.96.ff.ae
inet addr 10.1.1.5
bcast255.255.255.255.mask 255.0.0.0inet6 addr: fe20::208:2ff:fe96:ffae/64 scope Link
RX packets:44 errrors 0
so that was the guts of the eth0

lo bit next
inet addr 127.0.0.1 mask 255.0.0.0 
no packets and no errors

Next command sudo chclient:
bunch of stuff then
DHCP DISCOVER 255.255.255.255 port 67 interval3
dhcpoffer from 10.1.1.1
dhcppack from 10.1.1.1
bound10.1.1.4

---

### Post by siroche on 2008-02-26
will try it - rebooting

---

### Post by siroche on 2008-02-26
SWEET it works. Thanks heaps

---

