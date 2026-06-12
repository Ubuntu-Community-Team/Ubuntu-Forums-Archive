---
title: "Internet Connection - please help"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by Bushcamp on 2005-10-16
I loaded Hoary a few months ago on a split drive in an effort to start to work my way around OS.  However I was never able to get the internet connection sorted and now am trying to do this.  I have spent the past 2 hours searching for a solution - tried all the suggestions from previous posts and none seem to work.

I suspect the Linux cant find my modem I found a command audax321 to check, but dont know where to write that command.  In the Network Config menu - I have a modem and ethernet listed but not configered but cant seem to get it to configer either - Unfortunately it is a real mission as I have to log out each time I want to come back onto Windows to look up on the net, so please give me very specific info and where to find it.  It seems to have found some IP stuff, but it looks wrong - not my Windows PC IP address - is this possible?  Also seems to have found one pop server (work) but not my main email/IP provider at home.  Please help - I really want to get this sorted out or I will never get my head around OS.

---

### Post by ecobuntu on 2005-10-16
are you trying to use your modem or ethernet card?  what is your ethernet card?  are you running kde or gnome?

---

### Post by Bushcamp on 2005-10-16
Okay - that's way too technical already.  I'm running on a modem and I think it is on gnome.  How can I check?

---

### Post by Kapre on 2005-10-16
[QUOTE=Bushcamp]I suspect the Linux cant find my modem [/QUOTE]
I would assume from your post that you're using an internal modem. If this is true, you may want to identify your modem 1st by using this [thread]("http://www.ubuntuguide.org/#identifymodemchipset")

> It seems to have found some IP stuff, but it looks wrong - not my Windows PC IP address - is this possible?  Also seems to have found one pop server (work) but not my main email/IP provider at home.  Please help - I really want to get this sorted out or I will never get my head around OS.

I think that this IP address is your computers. Please provide more info as to what type of connection you have for the internet (this is assuming that you have another connection other than dial-up).

K

---

### Post by Bushcamp on 2005-10-16
Okay, I have an internal modem - Conexant 56k ACLine modem.  I am on dial up.

According to my IP address on windows it is 195.##.###.## but on ubuntu is was 127.00 something number.

I've found some more info - I dont know what it will tell me, but hopefully will give me more information on what the problem is.  I am going do a sudo modprobe usbnet and a ifconfig cat /etc/network/interfaces.  Will that help?

---

### Post by Bushcamp on 2005-10-16
Did the modprobe usbnet and got nothing - did not seem to register the command.

on the ifconfig command I  got the following

eth0   Link encap:  Ethenet Hwaddr 00:0F:20:##:##:A#
         itent6 add fe80::20f:  etc  64 scope link

UP Broadcast mulitcast MT etc

and  then

lo      link encap: local loopback
intnet address: 127.0.0.1  Mask 255.0.0.0
Int6 add :: 1/128 scope host

then on cat /etc/network/interfaces

loopback network interface
auto lo
1 face lo inet loopback

primary iface eth0 1net dhcp


In the network settings it says that that the model connection is not configured.
The ethernet connection is active (sorry- I guess I have got ethernet link)
Config DHCP
IP address, mask and gateway address are blank and wont let me enter (ie blocked)
In the General tab is says host is ubuntu and domain name is blank
on DNS tab, the server is 192.168.##.# (not the same as IP address on MS XP) and there is a search domain for my work remote web access
On the host tabs :
ff00:0 ip6-mcastprefix
127.0.0.1  localhost. localdomain local host ubuntu
fe00 :: 0 ip6-localnet
etc

any help?

---

### Post by Bushcamp on 2005-10-17
I found a really useful thread on setting up a dial up, which pointed me to the wiki.  I've followed all the instructions, but Ubuntu does not seem to recognise or find my modem.  How can I correct this?

---

### Post by Bushcamp on 2005-10-18
Two days later, I still cant get my dial up to work and feel like giving up.  Went up on a drive around town yesterday with my laptop to all the computer stores trying to find someone that knows OS and all I got was "we're MS people and you're finding out why" - Please let this be wrong,  please will someone help me cos so far these forums have not got me anywhere.:(

---

### Post by az on 2005-10-18
[QUOTE=Bushcamp] "we're MS people and you're finding out why" - Please let this be wrong,  please will someone help me cos so far these forums have not got me anywhere.:([/QUOTE]

You need to buy drivers for your modem from linuxant.com

They are one of the only companies to not release specs so that others can make the driver for linux for their hardware but make the driver themselves and *sell* it to you.  They do not understand opensource and I would encourage you to not buy a computer with their kind of modem in it in the future.

And the "MS" people you spoke to never logged on to forums like these....

---

### Post by Bushcamp on 2005-10-18
Thanks, are you saying I dont have the correct drivers for Ubuntu - how can you tell - what do I look for?

I will do that if I need to but would like to understand how you figured that out so that I can learn a bit more about what I'm doing and what I should be looking for.  Also because I am buying a new laptop next month and would like to understand what I need to look for.

---

### Post by DrinkYourOvaltine on 2005-10-18
I won't be much help as I'm new to linux myself but it looks like your particular modem will be troublesome to get working properly with linux. With dsl/cable being the prevailing choice for most computer users these days it may not be too difficult to scrounge up a free dial-up modem from a friend that will be more linux friendly. Ask around, and good luck.

---

### Post by Kapre on 2005-10-18
[QUOTE=Bushcamp]Thanks, are you saying I dont have the correct drivers for Ubuntu - how can you tell - what do I look for?

I will do that if I need to but would like to understand how you figured that out so that I can learn a bit more about what I'm doing and what I should be looking for.  Also because I am buying a new laptop next month and would like to understand what I need to look for.[/QUOTE]

Bushcamp - You already answered your question as to "how can you tell that I dont have the correct drivers?" - on your 3rd thread - you stated that you have a conexant 56k ACLine Modem.  Ive already checked the site and [here]("http://www.conexant.com/support/md_driverdownload.jsp") is the download page for the driver (please read the disclaimer first). I've also found this [howto]("http://www.tldp.org/HOWTO/Conexant+Rockwell-modem-HOWTO/") for you to read to give you more info on your kind of modem.

K

---

