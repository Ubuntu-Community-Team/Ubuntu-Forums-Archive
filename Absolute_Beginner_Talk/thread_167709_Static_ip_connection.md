---
title: "Static ip connection"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by N3wtR0ckn13 on 2006-04-29
I can not resolve any connection whatsoever with a static ip connection. my router is set dhcp(hyperwrt -v) and i have a layer2 switch. no connection, nothing. 
----------------------------------------------------------------------------
I've checked:
/etc/network/interfaces //configured for static ip and virtual-ip
/etc/hosts //localhost local domain etc
               //part of my problems tonight might be my dns server which isn't recognizing the temporary .com domain set. 
----------------------------------------------------------------------------
also, i'm getting access denied on all accounts when i type in various ip's into the browser weather dhcp or other.

---

### Post by htinn on 2006-04-29
Okay. Why is your interface configured for static IP if your router is using DHCP? Shouldn't the interface be using DHCP?

---

### Post by jorn on 2006-04-29
> Okay. Why is your interface configured for static IP if your router is using DHCP? Shouldn't the interface be using DHCP?
One can use static ip although the router is set up to deliver ip's at request.
N3wtR0ckn13. 
What are your settings fot static ip? Your routers ip?
Jorn

---

### Post by N3wtR0ckn13 on 2006-04-29
[QUOTE=jorn]One can use static ip although the router is set up to deliver ip's at request.
N3wtR0ckn13. 
What are your settings fot static ip? Your routers ip?
Jorn[/QUOTE]

my server is set to:
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

auto eth0:0
iface eth0:0 inet static
        address 192.168.0.101
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

my router is set to dhcp w/ static ip's start at .100
-------------------------------------------------------------------------
i was under the impression this shouldn't be a problem unless it's a dns issue of some sort. i'm using bind9. thanks for posting anyways.

---

### Post by htinn on 2006-04-29
No offense, but I don't see how that can work.

If your router is running a DHCP server, it needs to connect to a DHCP client. Static IP configuration will not work.

---

### Post by N3wtR0ckn13 on 2006-04-29
[QUOTE=htinn]No offense, but I don't see how that can work.

If your router is running a DHCP server, it needs to connect to a DHCP client. Static IP configuration will not work.[/QUOTE]

i have a linksys router wrt54g w/ hyperwrt firmware. under advanced routing you can assign the router to look for a static ip address too. i don't know though, maybe i'm interpreting that wrong.

---

### Post by LoclynGrey on 2006-04-29
So does this mean that your internet connection is a Dynamic IP from your ISP and you want to use the Linksys static IP function so that you can run a web/file/game server?

---

### Post by DSn0wMan on 2006-04-29
In my experience you should set the client and router to dhcp.

Then set your router to allways give a specific ip address to that client based on mac address.

---

### Post by N3wtR0ckn13 on 2006-04-29
[QUOTE=LoclynGrey]So does this mean that your internet connection is a Dynamic IP from your ISP and you want to use the Linksys static IP function so that you can run a web/file/game server?[/QUOTE]

i don't have a dynamic ip, but can obtain a mac address of my server no prob to set one up. my server is internal, but i'd like to ssh into it. trying to locate the connection through the router is just something i'm trouble shooting. i know the dns isn't listening nor is sendmail or anything else functioning. i've had a fsck.ext3 error too on start up losing gnome all together.

---

### Post by LoclynGrey on 2006-04-29
Are you running any firewalls on your machines?
If so, have you allowed access from your local network?

---

### Post by N3wtR0ckn13 on 2006-04-29
[QUOTE=DSn0wMan]In my experience you should set the client and router to dhcp.

Then set your router to allways give a specific ip address to that client based on mac address.[/QUOTE]

servers should be set statically at least for security reasons if not for connection. dhcp allows the absense of client connection without the duplication of assigned addresses and more trouble shooting on my end. nevertheless i'd set that range regardless and the max number of connections is alloted to 50.

---

### Post by N3wtR0ckn13 on 2006-04-29
[QUOTE=LoclynGrey]Are you running any firewalls on your machines?
If so, have you allowed access from your local network?[/QUOTE]

i have not enable iptables yet, but hmm...i havn't considered that yet and have little experience. i wouldn't even know where to look actually either since it's not wildly used i don't think. any command reference you could give me would help.

---

### Post by N3wtR0ckn13 on 2006-05-05
[QUOTE=N3wtR0ckn13]i have not enable iptables yet, but hmm...i havn't considered that yet and have little experience. i wouldn't even know where to look actually either since it's not wildly used i don't think. any command reference you could give me would help.[/QUOTE]

okay, so the default gateway was hanging me up greatly. if your gateway on your static ip is assigned differantly than your gateway behind the firewall, you'll get no internet service whatsoever. the default gateway on a linksys wrt54g is 192.168.1.1 and upon installation, ubuntu defaults at 192.168.0.1. 

good luck.

---

