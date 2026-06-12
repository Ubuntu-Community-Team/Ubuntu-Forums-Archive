---
title: "http://localhost.com/"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-16
I was just wondering, what is the IP address of [http://localhost/](http://localhost/) 
I just configured azureus and when I type my external IP address to access azureus Swing Web Interface, nothing happens. I type
xxx.xx.xxx.x:6883 where the "x" are my external ip address and nothing happens. But when I type localhost:6883 it works like a charm. What's the difference. I thought the external IP Address was the localhost. If not, what is the IP Address of the localhost.

:confused:h34r: Jaygo333 :confused:h34r:

P.S. Something's telling me of 127.0.0.0 has sometthing to do with this.

---

### Post by dueY on 2006-01-16
[QUOTE=Jaygo333]I was just wondering, what is the IP address of [http://localhost/](http://localhost/) 
I just configured azureus and when I type my external IP address to access azureus Swing Web Interface, nothing happens. I type
xxx.xx.xxx.x:6883 where the "x" are my external ip address and nothing happens. But when I type localhost:6883 it works like a charm. What's the difference. I thought the external IP Address was the localhost. If not, what is the IP Address of the localhost.

:confused:h34r: Jaygo333 :confused:h34r:

P.S. Something's telling me of 127.0.0.0 has sometthing to do with this.[/QUOTE]

I think 127.0.0.0 is the localhost.

---

### Post by Jaygo333 on 2006-01-16
[QUOTE=dueY]I think 127.0.0.0 is the localhost.[/QUOTE]

A little more clarification please.1?1

---

### Post by Estariel on 2006-01-16
no, 127.0.0.1 is the IP adress iof localhost.

127.0.0.1 always points to the machine you are sitting at.

Entering the external IP adress (the IP adress of your machine on your network) probably does not work, because the azureus interface maybe does not accept external connections. If that is the case, it should be possible to configure it in a way in which it does accept external connections.

---

### Post by Jonne on 2006-01-16
Any ip address starting with 127. are localhost, except 127.0.0.0, apparently. Usually the 127.0.0.1 address is used.

[http://en.wikipedia.org/wiki/Localhost](http://en.wikipedia.org/wiki/Localhost)

---

### Post by hen3rz on 2006-01-16
Ok heres how i see it i think i know what the problem.

The internal IP address of [http://localhost](http://localhost) is 127.0.0.1

The reason why the azureas web interface only works when u go to [http://localhost:6883](http://localhost:6883) and not when u go externalip:6883 is because you have niot opend that port on your firewall.

To open it up the port on your firewall simply go here and look up your modem/router:[http://www.portforward.com/routers.htm]("http://www.portforward.com/routers.htm")

---

