---
title: "domain names"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by zombietls on 2006-08-25
ok here is my question i bought this domain name [www.thedigitalevolution.net](www.thedigitalevolution.net) how would i connect this with my server from home so i can host my own webserver. 

thanks

---

### Post by Endwin on 2006-08-25
Assuming the place you registered the domain name with is also handling your DNS lookup just have them point the domain name to your IP, and wait a day or so for that information to propagate to other domain controllers. On your end make sure (if you have a router) to have port 80 forwarded to your server. 

That is really all that needs to be done.

---

### Post by mssever on 2006-08-25
You need to make the appropriate DNS entries to point the donain name to your machine. Contact your ISP for details. And you should have a static IP address--which few ISPs provide by default.

I wouldn't recommend hosting your domain on your own machine unles you're willing and able to ensure 99% uptime, good security, and really fast upload speeds.

EDIT: If you have a dynamic IP (using DHCP or something), you'll have to taks extra steps to make sure that your domain doesn't break when your IP changes.

---

### Post by zombietls on 2006-08-25
> **Endwin said:**
> Assuming the place you registered the domain name with is also handling your DNS lookup just have them point the domain name to your IP, and wait a day or so for that information to propagate to other domain controllers. On your end make sure (if you have a router) to have port 80 forwarded to your server. 

That is really all that needs to be done.

were do i get my ip from would it be by going to [http://www.whatismyip.com/](http://www.whatismyip.com/) or by using my home ip im not much of a networking person but im trying to learn, and also i think that the place that i bought my domain from allows me to control the ip adress for the name.

---

### Post by mssever on 2006-08-25
> **zombietls said:**
> were do i get my ip from would it be by going to [http://www.whatismyip.com/](http://www.whatismyip.com/) or by using my home ip im not much of a networking person but im trying to learn, and also i think that the place that i bought my domain from allows me to control the ip adress for the name.

whatismyip.com will tell you what your current IP address is. However, you need to find out if your IP is static or dynamic. Your ISP is the one to ask about this. Servers need a static IP (one that never changes)--although I've heard of paid services that make dynamic IPs work.

Once you've determined that your IP is static and what it is, you need to make the appropriate changes with your domain registrar. The registrars I've used actually point the domain name to your host's DNS server. If this is the case and you're self-hosting, you can either work out the DNS details with your ISP or run a DNS server yourself (quite advanced).

Use Wikipedia to learn about the various technologies at play.

---

