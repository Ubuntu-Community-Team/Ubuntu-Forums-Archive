---
title: "unable to restart apache2"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by caffienefree on 2007-04-17
When I attempt the restart apache,
> sudo /etc/init.d/apache2 restart

I receive the following error:
> 
 * Forcing reload of apache 2.0 web server...
 apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs                   [fail]

Searching on google hasn't given me a clear idea of what to do. Does anyone know the cause and fix for this? Thank you in advance.

---

### Post by joft on 2007-04-17
Sounds like you already started another daemon, which occupies port 80 . You can use netstat with the argument -anp to get a list of sockets/connections:

```

sudo netstat -anp | grep '^tcp.*LISTEN'

```

The last column of the output shows you the name of listening daemons/programs. The forth column also contains the ports they are listening on.

---

