---
title: "No internet after restart, must type dhclient to get internet"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by pencil86 on 2007-11-27
I'm running the latest version of Ubuntu under VMWare however if I restart Ubuntu, it loses the internet connection and I have to manually type in "dhclient" in terminal to get an internet connection. If I type ifconfig when theres no internet connection, it says my ip is 127.0.0.1. 

Why isn't Ubuntu getting an IP automatically from the router (dhcp enabled) and instead I have to type in dhclient?

---

### Post by alan34 on 2007-11-27
Hi have a look in /etc/resolv.conf for a nameserver.

sudo cp /etc/resolv.conf /etc/resolv.conf_backup

sudo gedit /etc/resolv.conf

mine is

nameserver 192.168.0.1         

which is the ip address of my router

Yours should look similar.

Otherwise (not sure about this) have you tried sharing the Vmware network address - you will
have to look in Vmware settings I think there is three setting you could try.

---

