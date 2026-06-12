---
title: "DHCP, Gateway, Firewall, DNS Server"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by mrordaz on 2007-05-31
Hi to all. Newbie here.

I am trying to setup an ubuntu server for  DHCP, Gateway, Firewall and DNS (all in one) to provide these services to workstations running windows.  I was able to setup the DHCP server and am getting an IP on a workstation but I cannot go out to the internet using that workstation. I can't even ping the IP address of the DHCP server. I can ping sites using the server though. (The server has two NIC cards, one facing internet and one facing local network) 

PLEASE HELP ME. Thanks.

---

### Post by dave-5B on 2007-05-31
have you set the gateway of the workstation to the address of the server?
although if you cant ping the server it soulds like although your workstation has an ip address, the server didnt give it out, theres no router on your network that could be acting as a DHCP?

if you give some more info about exactly how you have everything set up then people with more knowledge than me will be able to help you (i just used static ip addresses on my network to avoid this altogether :( )

---

### Post by mrordaz on 2007-06-01
Thanks for the reply.

I was able to access the DHCP server. I tinkered with the iptables. I still have a problem though.  I cannot access the internet from the workstation.

eth0 
  live.ip.address.1
  gateway.ip.address.1

eth1
  local.ip.address.1
  

eth0 is the static IP to Internet from provider

eth1 is the NIC connected to LAN with IP address 192.168.1.254.

Should I set a gateway address for eth1? what should it be?

Do I need IP masquerading?

---

