---
title: "Apache + Webmin + GoDaddy Domain = ???"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-10-07
I have Webmin 10, Apache 2.2.3, and am getting a GoDaddy domain, how do i make godaddy work with apache, so that apache knows about my domain...?

---

### Post by malan_in on 2007-10-08
hello,
   i am not able to understand clearly, u have a domain in godaddy, where do u installed apache and webmin ?

It is in same server or different server? where did u hosted for that domain ? do u have any static ip?, dedicated server?

---

### Post by kevin11951 on 2007-10-08
i have a domain through godaddy, but own a homebrew ubuntu 7.04 server... and run web min... so how do i get the godaddy domain to work on my home server? also it is a dedicated server, and static ip (or which ever one never changes) and i am behind a router, which ports 80, 8080, and 21, and my ISP leaves all ports open

---

### Post by tronica on 2008-03-27
did you get this figured out, im in the same boat

---

### Post by Oldsoldier2003 on 2008-03-27
> **kevin11951 said:**
> i have a domain through godaddy, but own a homebrew ubuntu 7.04 server... and run web min... so how do i get the godaddy domain to work on my home server? also it is a dedicated server, and static ip (or which ever one never changes) and i am behind a router, which ports 80, 8080, and 21, and my ISP leaves all ports open

Pretty simple. you tell godaddy your ip address and they add it to their dns servers. If they don't then you transfer your domain to a registrar that isn't trying to rip you off ;)

---

### Post by iSplicer on 2008-03-27
You need to register your IP address with a DNS server

---

### Post by Oldsoldier2003 on 2008-03-27
> **iSplicer said:**
> You need to register your IP address with a DNS server

yes and no.. for it to work the dns server has to be the SoA for that domain or the info wont propagate correctly.

---

### Post by matt79 on 2008-06-13
I have a home server that is using a godaddy domain name. However, it does not work like a real webpage to a really experienced user. But most would not reconize it I only happend to come across it. I have a ip address that changes when ever my ISP feels like I have had it to long:confused:. That is the tricky part about setting up a server with godaddy. How I did it is I have my server linked to a service that will automatically update my ip address at the times I set it to. It up dates it to a subdomain name that they have linked to my server. I then set up my godaddy domain name to forward all requests to the subdomain name that is with the automatic update. I also mask my godaddy domain name so it will be displayed in the address bar. And I do not have to register my IP address.:guitar:

---

### Post by Mech13 on 2008-06-17
Ok, so now that GoDaddy has my static IP address in its DNS servers. The website is being sent to my home server. Do i need to set up Apache Webserver on my home server? If I do need to, how should i configure it? Right now it is giving me the error:
"apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" 
But the website is working when i put in the [www.---.com](www.---.com)

Please help

---

### Post by matt79 on 2008-07-20
check this link out it might be what you are looking for. (although I am not quite sure what you are asking)
[http://ubuntuforums.org/showthread.php?t=658189](http://ubuntuforums.org/showthread.php?t=658189)

---

