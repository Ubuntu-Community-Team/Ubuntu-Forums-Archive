---
title: "Can not connect to internet, multiple static ips"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by abrianb on 2007-09-06
I am having trouble getting my laptop to connect at work. It connects fine at home. At work I connect to a netopia router.The laptop is an IBM T-20 running Ubuntu 6.06lts.The provider is AT&T yahoo dsl. The account provides static IPs first usable xx.xxx.xxx.233 to xx.xxx.xxx.237. I have tried using the network settings, I created a location (work), set it as an Ethernet connection,plugged in the DNS info. No Go. Tried setting it up both DHCP and static. Neither worked. When I list the Ip address their is only a blank for one.This system uses multiples and I think that might be the problem. I hope someone can help. Thanks.

---

### Post by nitro_n2o on 2007-09-06
just to make this clear... 
you want to connect to a wireless network, right? 
if yes, then you don't have to set up and Ethernet connection
what is the output of the command "iwconfig" in the terminal? 
it might be that you ran out of address in  your work and thus you can't connect...

---

### Post by irish_flu on 2007-09-06
Are there other machines (already there and plugged into the same router) that work? I'd start by making sure your settings are compatible with theirs.

If there's a known good cable, I'd also try that (just in case you're using a bad cable, unless you're using the same cable you use at home of course).

---

### Post by abrianb on 2007-09-06
I am trying to connect to a wired internet connection. The connection works. I am running a ethernet cable from the laptop to the Netopia router. The router works and other computers on the router have internet connection. The router is hooked to the phone company on a phone line thats dedicated for ADSL. Hope that clears up somethings about the connection.

---

### Post by Iowan on 2007-09-06
Is it possible that IPv6 is causing a problem?

---

### Post by abrianb on 2007-09-06
It could be, I am not real familiar with this system. More details might help. Thanks

---

### Post by WebSiteGuru on 2007-09-06
Ask your office! Also, it can also be that your work have proxy server to direct web traffic. Then you will need to put that to your default gateway.

---

