---
title: "internet access from feisty to laptop with vista"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by ubuntosh on 2007-11-10
hi there, I have my desktop with Feisty installed and I access the internet through a linksys wireless card, in the office. My co worker has a laptop with windows vista installed but has no wireless card and  I want to give him access through my desktop using the ethernet connection. How can I do this with Feisty?

We already did it with our boss's laptop, which has wireless conectivity and it runs windows XP, connecting both laptops, worked well and the setup was easy, but I haven't been able to do it with my desktop.

We connected both computers already, the connection was successful, both computers showed it but my friend cannot browse the internet through my connection. 

:(

---

### Post by Pumalite on 2007-11-10
Better get a router and install a LAN

---

### Post by HermanAB on 2007-11-10
I agree that it is best to spend $40 on a Linksys, Netgear or Dlink 'Home Router' at Staples or Best Buy, to provide net access for the whole office.

However, that being said, if your Linux box has two ethernet ports, then you can install Firestarter on eth0 and run the following commands to NAT the second port, effectively turning your PC into a router:

```
# Bring the 2nd ethernet port up
ifconfig eth1 192.168.1.254 netmask 255.255.255.0 up

# Enable IP forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

# Create a NAT firewall
iptables -I FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -I FORWARD -i eth1 -o eth0 -j ACCEPT
iptables -t nat -I POSTROUTING -o eth0 -j MASQUERADE

```

Then plug the other PC into eth1 using a switch or a cross-over cable, set its IP address to something in the subnet 192.168.x.y and its default gateway to 192.168.1.254.  Alternatively, run dhcpd on the Linux box.

I sometimes use my laptop to connect to my WiFi router and then plug a second device into the ethernet port of the laptop through a cross-over cable and then use the above trick to enable  a little Desktop LAN.

Herman

---

