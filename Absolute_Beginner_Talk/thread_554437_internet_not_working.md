---
title: "internet not working"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by deroldj on 2007-09-19
I am fairly new to linux and ubuntu, and have looked in th ubuntu documentation, common questions and community documentation, and found no answers that worked. I installed Ubuntu 7.04 and could not get the internet to work, and then tried on the live cd, stilll no work. I have windows installed on the wsame computer, and internet works on it.

I have a Netopia router style modem,  networks settings are at DHCP, and am wired through ethernet connection. Top right of desktop shows connection icon, which says wired network connected..network interface ETH0, speed 100mb/s, driver 8139too.

I ran PPPOECONF and found eth0 then said network connection failed, cannot assign requested address. I tried to manually set the network, but that also failed.

---

### Post by sunexplodes on 2007-09-19
You're going to have to give us a bit of information.

Wired? Wireless? Router? Modem? Did the internet work before, and STOP working, or has it NEVER worked with Ubuntu?

---

### Post by Wim Sturkenboom on 2007-09-19
> I am fairly new toI can see that :) Your post is missing every piece of information that is required to be able to get help.

First of all, what are the symptoms?

Next wat type of connection (phone, dsl modem, ...). What make/model of modem? How do you connect modem to computer (serial, usb, ethernet, ...). Any other equipment involved like a router?

What did you do to setup your connection?

---

### Post by deroldj on 2007-09-19
I think those questions were answered in the secound paragraph, but maybe not so I will try again. It is a wired ethernet connection. I have a Nettopia modem, I beleave it is a router style, as log in and pass word are kept in modem. Yes the internet still works in windows, and puppy linux, so it is a Ubuntu problem. I had an older version of Ubuntu, and it connected as soon as I installed it. It is a DSL connection. 

The symtoms are, according to Ubuntu I have a network connection, but when I open fireox, I get no internet

I followed all the basic steps to set up a dsl connection , then all the pppoe steps.  When I went to admin>network my eth0 connection is shown and active, and set for dhcp. I did try setting it manually, but that did not help

---

### Post by deroldj on 2007-09-19
I ran       /etc/network/interfaces
   I had

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

notice no address or netmask. I tried entering them with gedit and sudo, but hey did not help


I ran     pppoeconf
  and got

found eth0 and eth0avah
then said
access concentrator of your provider did not respond

I checked eth0 configuration, and looks ok, left at dhcp
I checked eth0avah and said no such connection, does not exist

---

### Post by deroldj on 2007-09-19
suppose if this is not repairable, I can just go back to an older version o ubuntu, or back to suse:(

---

### Post by deroldj on 2007-09-19
still not working, can anyone help here

---

