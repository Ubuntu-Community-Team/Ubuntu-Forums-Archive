---
title: "Wireless Firewall/Router with OpenVPN and NAS"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by drum4god917 on 2007-12-30
Well, I have been doing some research and I am wanting to create a network similar to this person's setup: [http://ubuntuforums.org/showthread.php?t=346059&highlight=openvpn+nas]("http://ubuntuforums.org/showthread.php?t=346059&highlight=openvpn+nas")

The difference is that I would be using a dedicated wireless card to connect the clients, and there's no community wireless, just an ethernet hook up.

```

Internet
    |
UbuntuServer --(Gigabit Switch)-- Encrypted NAS
    |
(Wireless via OpenVPN)
    |
MacBookPro, and any other wireless clients

```

I would like to be pointed in the right direction of how to do this and if there's a better way. I am holding off on buying the needed components until I find out if I can do it or not. :confused:
The reason for the switch is if I needed to transfer some huge macho files in a hurried-like fashion, I would tether my MPB using ethernet, directly to the NAS, if that setup is possible. Would there also be anyway to access the NAS through the server, from the internet side, using VPN when I'm away?

Any and all help would be greatly appreciated. Thanks in advance.

---

### Post by rivalarrival on 2008-01-01
Basically, you're trying to turn your server into a NAT router. It's pretty routine, really. 

You are going to have three real network adapters and at least one virtual one - the VPN connection. You can use Shorewall to set up NAT routing on all four connections. I've found it's pretty easy to configure Shorewall using Webmin.

Webmin is a tool that allows you to administer a server from a web browser. It is a very powerful tool.

Shorewall is a router/firewall application with a ton of configuration options. The webmin module for shorewall makes configuration a breeze. There are several how-to's that cover shorewall with nat routing.

Webmin will also manage PPTP and OpenVPN server packages - I've never used OpenVPN myself, but I've had good luck with PPTP and windows clients.

I assume you're using the OpenVPN links as additional security on the wireless network? You'd just firewall the wireless connection and the internet connection, open the ports on both to your VPN server, and use NAT routing on the internet connection to the virtual, VPN adapter and the other ethernet adapter to your NAS.  You'd have access to the NAS from the gigabit switch, the server directly, or any VPN clients attached, but not from the internet, and not from any person who managed to connect to your wireless but not the VPN.

---

