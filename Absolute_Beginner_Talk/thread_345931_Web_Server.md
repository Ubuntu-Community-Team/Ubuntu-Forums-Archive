---
title: "Web Server"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by pacco on 2007-01-24
I was wondering if there was anyway to make a web server and post it to the web without having a domain,for example if i wanted to make a forum locally on my system,would people on the inetrnet be able to post to this forum?

Kind of a dumb question i guess
:) 
Thanks in advance,
pacco

---

### Post by ronnieredd on 2007-01-25
*Kind of a dumb question i guess*
No such thing.
A couple of things we'll need to know is:
[LIST]
[*]Do you have a router or are you directly hooked to the cable/dsl modem?
[*]Do you know how to port forward on the router?
[*]If you don't have a router, get one.
[*]Do you have a static or dynamic IP address with your ISP?
[/LIST]
Once we know these things it'll be easier. You can get a domain from 1and1 pretty cheap and I use zoneedit.com for dns pointing. That said you could always point everyone to to an IP address only, although I would recommend against it. If you're on a dynamic IP, then no one would be able to bookmark it and you'll other issues like that.

---

### Post by rccharles on 2007-01-25
> **pacco said:**
> I was wondering if there was anyway to make a web server and post it to the web without having a domain,for example if i wanted to make a forum locally on my system,would people on the inetrnet be able to post to this forum?

Kind of a dumb question i guess
:) 
Thanks in advance,
pacco

You may want to look into a dynamic dns address.  Do a google search for:
dynamic dns

Here are a few links:
[http://www.dyndns.com/](http://www.dyndns.com/)
[http://www.no-ip.com/](http://www.no-ip.com/)

More info on topic:
[http://www.technopagan.org/dynamic/](http://www.technopagan.org/dynamic/) 

If you have static IP address, you can type in the IP address.  You may have to pay extra for this.  


While getting a Domain Names isn't too expense they generally require a static IP address.

Robert

---

### Post by lingnoi on 2007-01-25
You can [install a webserver with PHP and MYSQL]("https://help.ubuntu.com/community/ApacheMySQLPHP") (what you need to install a php forum).

You don't need a domain name but you will need a static IP address.

---

### Post by pacco on 2007-01-25
yeah i have a siemens speedstraem 6520,i have dsl service,i know how to forward ports.
And i can set ubuntu to a static ip address,i believe i do have a static ip address through frontier.

Thanks
pacco

---

