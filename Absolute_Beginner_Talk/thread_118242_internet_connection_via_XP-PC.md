---
title: "internet connection via XP-PC"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by Geniedesalpages on 2006-01-16
hello

I have installed ubuntu on my laptop and windows XP on my desktop pc.

There is a connection between them two via the serial port. How can I configurate my ubuntu to get to the internet via my desktop pc?

I made a connection thingy on the xp for the serial port and tried with slattach tty to establish a connection to the xp. But it didn't do anything (hung..). XP doesn't "see" the ubuntu neither.

Thanks for the help

---

### Post by Mr_Grieves on 2006-01-16
First off, don't use your serial port for this. Use an ethernet port and a regular straight network cable.

When you've connected the two computers you need to put them on the same IP network. This setup suggests you only have these two computers connected together and not other networks.

Example:

Laptop with Ubuntu Linux
IP-adress: 192.168.0.1
Netmask: 255.255.255.0
Default gateway 192.168.0.2

Desktop with Windows XP
IP-adress: 192.168.0.2
Netmask: 255.255.255.0
Default gateway: 192.168.0.1

If you want to connect the two computers together AND have access to Internet I highly recommend that you buy a simple home router. It's not that expensive either.
Netgear produces cheap routers with high quality for this purpose.

---

