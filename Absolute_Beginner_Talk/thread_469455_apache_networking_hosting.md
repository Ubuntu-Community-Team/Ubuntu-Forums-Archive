---
title: "apache networking hosting"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by stonerrob420 on 2007-06-09
I've got home network with a windows xp computer connected to the internet and it is hooked to my ubuntu dapper computer by a 25 foot crossover cable. I have apcahe 2 installed on my ubuntu computer. The windows xp computer is sharing its internet connection with the ubuntu dapper computer. How can I setup the systems  where the outside world can see the html page?. I've already got the index.html file written and ready with all the graphics....

---

### Post by freebeer on 2007-06-10
Microsoft's ICS is a very poor substitute for a hardware router.  You'd be much better off buying a hardware router (Linksys, D-link, etc.) than trying to forward ports through ICS, imho.

---

### Post by stonerrob420 on 2007-06-11
I can set the ICS in windows to accept a new service such as the apache 2 on my ubuntu computer but what ports does the apache http server listen on? How do I forward the ports on apache 2 on the ubuntu computer?

---

### Post by freebeer on 2007-06-11
apache (default) listens on port 80.  I don't think you need to forward ports from apache... you need to forward  port 80 from ICS to the IP address of the apache server.  That should do it.  (Outgoing ports aren't generally blocked... only incoming.)

---

### Post by stonerrob420 on 2007-06-12
Thank you very much for the information...I'll give it a try and see how it works....I'll post back and let you know how it went...hopefully it will go good ;)

---

