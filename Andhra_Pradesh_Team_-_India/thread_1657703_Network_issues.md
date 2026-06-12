---
title: "Network issues"
date: 2011-01-01
forum: Andhra Pradesh Team - India
---

### Post by shuvra on 2011-01-01
Hi!

Happy New Year!

I have an IBM Thinkpad T60 (which I have been using since July 2006) and I have Ubuntu 9.04 installed on it.

I am right now visiting Calcutta on vacation and signed up for an ethernet connection and I need to configure stuff to be able to connect but unfortunately I have failed to do so.

My /etc/networks/interfaces looks like:
auto eth0
iface eth0 inet static
address 10.0.3.243
netmask 255.255.255.0
network 10.0.3.0
broadcast 10.0.3.255

and my /etc/resolv.conf file looks like:
nameserver 10.0.3.2
nameserver 4.2.2.3

After I restart my network with the command:
sudo /etc/init.d/networking restart

I am able to ping the network at 10.0.3.2 but when I click the network and choose the Auto eth0 (Wired Network) option, it returns the message "You are now disconnected".

Can you please help me?

Thanks a ton,
Shuvra.

---

### Post by solar george on 2011-01-01
/etc/networks/interfaces and the gui network settings do not work together well . . . unless you have a pressing need to use the text-mode settings you'd be much better handling it through the gui (just comment our all the eth0 lines except for auto eth0 in the interfaces file).

You can then use the gui to create a new network profile for eth0 and select that when you want to connect to the network in question.

EDIT: Whoops just noticed this is in a loco subforum (I found this via the forum search) hope no-one minds me posting here

---

