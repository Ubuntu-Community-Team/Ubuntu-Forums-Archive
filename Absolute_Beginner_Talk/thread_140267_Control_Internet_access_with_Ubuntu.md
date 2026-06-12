---
title: "Control Internet access with Ubuntu"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by B7may on 2006-03-05
Hi all,

I have a ADSL internet connection.  I have that connected to a 8 port router.  I then have 4 computers connected to the router for internet access.  All of the computers are running windows XP, except for 1 which I just installed Ubuntu on.  I have set up the Ubuntu machine to be a file server and a print server.  One thing I would like to make it do is control which computers have access to the internet.  I would like to have 2 of the computers only be able to access the Ubuntu machine and not be able to access the internet.  Is there a way to do this?

Thanks
Brian

---

### Post by soce_32 on 2006-03-05
It really depends upon your router.  You may be able to turn off incoming/outgoing access to certain IP/MAC addresses if it has some advanced firewall capabilities.

Your linux box can do what you want but you would need two network cards in it, setup routing with iptables and run your DHCP service from your Ubuntu box.  You would need to change your physical setup so that it goes like this:

ADSL Modem <-eth0-> Ubuntu Router <-eth1-> switch -> Rest of computers

You could then setup your box to do firewall/NAT/routing and create rules that basically drop all in/out traffic from the two computers that you do not want on the internet, but they will still be able to access your Ubuntu box and other machines on your home net.

---

