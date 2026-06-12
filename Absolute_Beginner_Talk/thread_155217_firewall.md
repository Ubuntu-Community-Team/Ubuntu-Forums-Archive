---
title: "firewall?"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-04-04
I'm having trouble getting amule and emule(using wine)
to work. amule tells me I'm lowid and I can't find a server. amule makes me lowid as well but if I keep restarting it again and again eventually I get a highid however after a while I lose my connection or kb rate just falls off or stops and all files sit waiting. Is this do to a firewall? I don't remember reading anywhere that ubuntu 5.10 came with a built in firewall, I thought you had to install that yourself (not that I think you need to) What do I do to get amule or emule working with high ID?:confused:

---

### Post by mzilhao on 2006-04-04
do you have a router? if so, you may have to forward the ports amule/emule uses... do you have windows installed on your machine?

---

### Post by wolfee on 2006-04-04
I have a router but I don't have microshaft on my hd (other than some programs for wine) How do I forward my ports?

---

### Post by tappad on 2006-04-04
Usually your router has an http interface..
so, enter [http://Ip.to.your.router](http://Ip.to.your.router) and se what happens.
I think the section your looking for is called NAT.
There you should be able to enter a port-number and an ip-adress that will recive all data on that port..

---

### Post by wolfee on 2006-04-04
[QUOTE=tappad]Usually your router has an http interface..
so, enter [http://Ip.to.your.router](http://Ip.to.your.router) and se what happens.
I think the section your looking for is called NAT.
There you should be able to enter a port-number and an ip-adress that will recive all data on that port..[/QUOTE]
 I cant find the IP # It has the model # and pin # but no Ip # should I go on line to find it or is ther a command from the terminal I should use

---

### Post by jamey on 2006-04-04
You may be able to find out your router's IP address using the following method:

System &#8594; Administration &#8594; Networking

Click the DNS tab. The first DNS server listed is more than like to be the IP address of your router, for example 192.168.1.254.

Then just use this address to access the router configuration... [http://192.168.1.254/](http://192.168.1.254/)

---

### Post by wolfee on 2006-04-04
it's not giving me anything but"cannot find server" message

---

### Post by dcstar on 2006-04-04
[QUOTE=wolfee]I cant find the IP # It has the model # and pin # but no Ip # should I go on line to find it or is ther a command from the terminal I should use[/QUOTE]
```
route -n
```
It is the Gateway IP.

---

