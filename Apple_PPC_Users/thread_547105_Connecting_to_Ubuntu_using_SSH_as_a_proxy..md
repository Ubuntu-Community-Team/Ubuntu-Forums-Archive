---
title: "Connecting to Ubuntu using SSH as a proxy."
date: 2007-09-09
forum: Apple PPC Users
---

### Post by joshbray on 2007-09-09
I have installed Open SSH on my linux box, but how can I connect to it using my Mac. I am trying to use it to get around the proxy at my school. So it would be my mac at school connecting to my linux box at home.

Thanks

---

### Post by pau13 on 2007-09-10
Configure you ssh server to use the 80 or 443 port (http or https). At the same in client.

---

### Post by joshbray on 2007-09-10
Ok how do I do that?

Also what username and password would I use to connect?

---

### Post by pau13 on 2007-09-11
If use Http_proxy with login and password:

Install corkscrew
sudo apt-get install corkscrew

Add in /etc/ssh/ssh_config
ProxyCommand /usr/bin/corkscrew proxy 8080 %h %p /etc/ssh/Autenticacion

And create /etc/ssh/Autenticacion
login:password

And use the 80 or 443 ports.

---

