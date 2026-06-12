---
title: "I need to know how to set up my internet connection"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Capra on 2006-08-25
hey,

Anyone know how to setup internet connection, i have broadband and i need user and password to connect, but i dont know set it up :S

cya

---

### Post by Jerome36 on 2006-08-25
I was going to ask for more details, but noticed you mentioned DSL in another post.  I too have DSL, and I had to initially access the DSL modem via a web browser, to enter my username and password.

If that's what you're suppose to do just open up Firefox and enter the IP address for the DSL modem (for me it was 192.168.1.1, but it could be different for you), and you should get the modem's setup page.  This is assuming you have to do the same.

---

### Post by Druidor on 2006-08-25
normally the user login & password reside within the modem/router.

I have only ever had a router on my broadband cconnection so this is how I set mine up

1. access the router its on ip 10.0.0.2 & put in the relevent login details.

on Dapper

System>Administration>Networking


Ethernet connection>Properties

Tick Enable this connection

Configuration: Static IP address
IP address: 10.0.0.5
Subnet mask: 255.255.255.0
Gateway address: 10.0.0.2

Under DNS

DNS Servers
195.8.69.7
195.8.69.12

This DNS information is from my ISP

I run 4 PCs off my router so all have static IPs so I can transfer between them, you may be OK with DHCP in that it gives out the ip as a pc comes on the network.

best advice is buy a router though they are so much better when you using multiple machines.

---

### Post by drtvasudevan on 2006-08-25
hi, follow druidor's instructions but just enable dhcp and it will automatically take care of net connection.
also try disabling ipv6 in firefox if you cant connect before seeking help again.

---

