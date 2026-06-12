---
title: "How to setup a DNS Server?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-04-19
Ok, I created a website, which works fine. [http://69.114.39.249:8258/](http://69.114.39.249:8258/) I bought a domain name, yet it wants a DNS for some reason, when I redirect it to my IP, it does not work, anyone have any tips?

---

### Post by koenn on 2007-04-19
when you try to browse the site by hostname, you will still have to include the port number ( 8258 )in the url.

---

### Post by aberry5555 on 2007-04-19
The company that you registered your Site on may have DNS facilities, I would check out the settings there.

Otherwise I would suggest installing "BIND" (linux DNS server, and the predominant software for DNS world-wide) and "Webmin", which is not in the Repos but can be found at [http://www.webmin.com/](http://www.webmin.com/) .

It's not particularly easy, though, to set up DNS if you don't know how, I would reccomend seeing if your web-name company can set it up for you. 

IF you need help in setting up your own BIND server then message back and I'll try and talk you through it, there are, luckily, sites that will test your DNS once it's set up to make sure it's not dodgy :p

---

