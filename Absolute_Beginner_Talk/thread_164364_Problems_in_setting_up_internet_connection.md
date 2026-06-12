---
title: "Problems in setting up internet connection"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Monsieur on 2006-04-22
Hi,

I have just installed Ubuntu on my laptop, but I'm having problems getting my internet connection up and running... The strange thing is that all network drives are correctly installed, and they even send and receive packets... I don't understand why, but I cannot use for example, the ping program, even though I send and receive the supposed packets... It goes on pinging, and doesn't get any reply.

Do you think it may be a DNS Server issue? On my DNS Servers list, I only have one listing, which I find a bit weird: 192.168.1.1. This being the localhost address, how can it be my DNS server?

BTW: I use a local router to connect to the internet ( it's fine, on Windows there are other computers using the same connection ) , and I'm using DHCP.

Thanks for any help!

---

### Post by jazzmuzik on 2006-04-22
I've had situation like that where ping doesn't work, but http via the browser does work. It could be a DNS, firewall or routing issue.

192.168.1.1 in /etc/resolv.conf is a reserved local address, so it cannot be correct. The value in that file should be your ISP's DNS server address. THe value may be placed there automatically by your modem/router or you have to add it yourself:

search myisp.net
nameserver xxx.xxx.xxx.xxx

However, one reason 192.168.1.1 may be valid is if you are running your own DNS server or a DNS caching system.

---

### Post by Monsieur on 2006-04-22
What do you have on DNS Servers? I find it very weird, to only have the localhost address in there...

---

### Post by Bloch on 2006-04-22
192.168.1.1 is the precise nuimber I have to use to connect to utv broadband on a Creative Boradband Blaster modem.
 I am no expert, but the way I have to connect (on windows and linux)
is opening a browser and entering
[http://192.168.1.1](http://192.168.1.1)
as the URL. Then you will be asked for a login and password. This should have been given to you - the default is 
admin

---

### Post by Monsieur on 2006-04-22
I just found a way to go around it... I don't know if it's considered a bug.

In order to gain internet access, I can only have either the wireless or the lan card, activated. With both of them on, I loose the internet connection. It is pretty weird... I don't really understand it, but I leave here the warning.

---

### Post by jazzmuzik on 2006-04-22
It sounds like Ubuntu is inserting the modem's DNS address, which is 192.168.1.1. And then the modem stores it's own set of DNS addresses. When you need DNS resolution your system points to the modem which retrieves the address and sends it back to your computer. 

My previous comment was incorrect.

---

### Post by Lord_Drakkus on 2006-04-22
Strange that it's 192.168.1.1, considering that usually that's reserved for routers/hubs/switches/etc. and the actual modem itself is set to 192.168.0.1 by default...

Try changing your DNS to 192.168.0.1 and see what that does.

---

