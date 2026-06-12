---
title: "view website from remote machine"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by blioux on 2007-03-06
hello all,

I am able to view my webpages, served by apache2, from the local machine but it doesn't come up from a remote machine. 

all i get is the:
-----------------------------------------------------------
404 Not Found 

Not Found

The requested URL / was not found on this server.
-----------------------------------------------------------

If i turn off apache2 then i get:
-----------------------------------------------------------
The connection has timed out

The server at 192.168.0.55 is taking too long to respond.
-----------------------------------------------------------

so it appears the request is being received by the server.... don't know what to check or what info to provide.

any help is greatly appreciated

thanx,
blioux

---

### Post by taurus on 2007-03-06
Is your machine connected to a router and did you remember to open that port in your router for outside traffic to get through?

---

### Post by blioux on 2007-03-06
thanx for the reply!

this is all on my local home network.

i am able to ping and get responses.

the fact that apache returns the 404 error tell me that apache it is accepting the request.

again, i am able to see the pages locally just not from another machine.

any other ideas?

---

### Post by blioux on 2007-03-06
when i check:
/var/log/apache2/error.log

i see:
[Tue Mar 06 17:33:09 2007] [error] [client 192.168.0.53] File does not exist: /htdocs

???

---

### Post by blioux on 2007-03-06
looking thru "apache2.conf" and "000-default" i do not see any reference to "/htdocs"

any ides?

---

### Post by blioux on 2007-03-06
fixed it!

changed:
<VirtualHost 127.0.0.1:80>

to:
<VirtualHost *:80>

---

