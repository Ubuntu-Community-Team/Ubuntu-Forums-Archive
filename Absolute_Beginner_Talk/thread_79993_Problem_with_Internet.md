---
title: "Problem with Internet"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by NoirDelire on 2005-10-21
Hello,

I'm new to linux and ubuntu. I did install it on my PC a few weeks ago. Every thing was fine. Then, my landlord changed the Internet router. He buy a D-Link one.

And my linux machine is gone our of order.

Well... the symptoms are stranges. On the win2k machines, everything is fine. But on the ubuntu's one, there are many internet sites I can't reach. It wait and wait, and... get no reply.

There are other sites, I can reach, however. And the lan is okay too. I can reach google, for exemple. And I can do a search on it.

I posted an help request on the french forum. Guys told me to try tu set my mtu value to 1400. But it changed nothing.

I tried the live CD on other PCs, with the same results. So, I'm convinced it's the D-Link router the guilty. But I can't change that one. So, how could I tune ubuntu to make it working ??

Thanks for your help.
Noir Délire

---

### Post by Psy-Q on 2005-10-21
Can you try doing the following:

Boot the windows machine and try to find out what it's using as IP address, subnet mask and gateway/router address. Also, take note of the name servers it thinks are appropriate.

Boot the Ubuntu machine again and take a look at the same information:

Start a terminal, enter "ifconfig", the entry under "inet addr" is your IP address. Enter "route", the IP in the "Gateway" column next to "default" is your default gateway (i.e. router). Then do "cat /etc/resolv.conf" to get the nameserver.

Are the nameserver, gateway and subnet mask the same on Windows and Ubuntu? They should be. The IP may differ, that's ok.

It's strange that you can reach some sites. The problem might be that your machine is using the wrong nameserver and still has a few old names that you use often (like google.com) cached. So the machine is getting a valid IP address and router information, but not name server. Just some speculation :)

---

### Post by NoirDelire on 2005-10-21
Hello,

Okay, here are the results.

With win2k, my ip is 192.168.1.2. My subnet mask is 255.255.255.0. My gateway is 192.168.1.1. And I think it's my name server too... but I don't know how to check it.

With ubuntu, my ip is also 192.168.1.2, My subnet mask is correct too, my DNS is 192.168.1.1, thus correct, but... my gateway is "*". No IP number.

Is it a problem ?

Thanks for your help,
Noir Délire

---

### Post by Psy-Q on 2005-10-22
Odd, you don't have a default gateway on the Ubuntu box? Can you try doing "sudo route add default gw 192.168.1.1" and see if the net temporarily works afterwards?

---

### Post by NoirDelire on 2005-10-23
Hello,

The command route did reply "SIOCADDR: Le fichier existe" which means that the file exist.

And it was not beter with firefox after that.

What can I do ?

Noir Délire

---

