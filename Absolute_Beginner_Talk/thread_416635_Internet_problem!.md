---
title: "Internet problem!"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by thorosius on 2007-04-21
Hy !
Although I am not new to Linux but I am new to Ubuntu. And I am facing the same problem as I did with other distros. The problem is I can't use Internet. At first I was trying to install the driver for my modem which I did but the modem wouldn't work so I abandoned this. Now I am trying to share an Internet connection with a WinXP machine but can't get it to work. WinXP machine has a static IP 192.168.0.1 and has a shared internet connection. Ubuntu machine gets its IP from WinXP machine by DHCP.
 
[CENTER]Internet
/\
||
||
<WinXP Ethernet IP:192.168.0.1 0>
OS:WinXP updated upto December 2006
Internet connection sharing enabled
This PC successfully connects to the internet.
||
Cross cable
||
\/
<Ubuntu EthernetIP:192.168.0.2>
OS: Ubuntu Edgy[/CENTER]

---

### Post by steve.horsley on 2007-04-21
Can you ping the XP machine? If so, you are probably missing two things - an IP route, and the addresses of hte DNS servers.

The IP route can be added with this command:
**sudo route add default gw 192.168..0.1**

The IP addresses of the DNS servers you will have to look at the XP box IP configuration and read the DNS servers addresses from there. Add these to the file /etc/resolv.conf, one address per line like this:
[B]nameserver 1.2.3.4
nameserver 6.6.6.6[/B]

---

### Post by deaster2 on 2007-04-21
> **thorosius said:**
> Hy !
Although I am not new to Linux but I am new to Ubuntu. And I am facing the same problem as I did with other distros. The problem is I can't use Internet. At first I was trying to install the driver for my modem which I did but the modem wouldn't work so I abandoned this. Now I am trying to share an Internet connection with a WinXP machine but can't get it to work. WinXP machine has a static IP 192.168.0.1 and has a shared internet connection. Ubuntu machine gets its IP from WinXP machine by DHCP.
 
[CENTER]Internet
/\
||
||
<WinXP Ethernet IP:192.168.0.1 0>
OS:WinXP updated upto December 2006
Internet connection sharing enabled
This PC successfully connects to the internet.
||
Cross cable
||
\/
<Ubuntu EthernetIP:192.168.0.2>
OS: Ubuntu Edgy[/CENTER]

Had the same identical problem in my office except I was using two XP boxes.
Couldn't get the internet box to share the connection with the other.
I had a usb connection to the internet with two nic cards and a crossover
cable to the nic cards. 
I found out, by reading Microsoft's knowledge bases, that I HAD to have
a nic connection to the internet, not a usb. Installed another nic card in
the connection sharing box to the dsl modem and everything was well.
Hope this helps...

---

### Post by Patrick K on 2007-04-21
If you have the Firestarter firewall installed. In Feisty it come preconfigured to block all outgoing traffic. Open it and go to the Policy page. Select outgoing. You will have a choice of "Restrictive" (the default) or "Permissive". In "Restrictive" you have to explicitly allow traffic. In "Permissive" you explicitly disallow traffic.  

I was locked off the Internet for many hours until I found this. Interestingly, Pings went through and were returned.

---

### Post by thorosius on 2007-04-21
Steve.horsly >> This solved the problem. I should have been here early! Thanks !

---

