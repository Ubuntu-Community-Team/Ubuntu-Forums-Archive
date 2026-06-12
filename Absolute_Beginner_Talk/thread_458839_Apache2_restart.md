---
title: "Apache2 restart"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by fulanitok on 2007-05-30
Hi guys,

I'm trying to get my Apache2 Web Server Public but don't really know how to do.

I've install the Apache2 package and all looks fine but when somebody try to connect to my server they don't get in, Can't find host or Can't find web pages error.

I try several times to restart my Apache Web Server but get this:

```

*******@*****-desktop:~$ sudo /etc/init.d/apache2 restart
Password:
 * Forcing reload of web server (apache2)...                                    apache2: apr_sockaddr_info_get() failed for *****-desktop
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: apr_sockaddr_info_get() failed for *****-desktop
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]

```

And another thing is the **httpd.conf** is empty, is that normal?

thx

---

### Post by verbatim210 on 2007-05-30
Yes, it is normal for httpd.conf to be empty because ubuntu uses apache2.conf instead.  

You sound like you have a network problem, test [http://localhost](http://localhost) to see if apache works first.

It is likely the public cannot access your server because your ports are closed.

Good luck

---

### Post by disruptor108 on 2007-06-21
I have this same problem.  I was trying to setup MythWeb to be accessible outside my LAN ([https://help.ubuntu.com/community/MythWeb](https://help.ubuntu.com/community/MythWeb)) and apache won't restart when I get everything configured.  I can still reach MythWeb for now, but I received the same error as fulanitok.  Any ideas?

---

### Post by jlk on 2007-06-21
Apache cannot determine what the default domain is.  You need to:
a) set up /etc/hosts
or
b) set up DNS

In both cases you need and IP address and a domain (ubuntu.com)

---

### Post by thomasconor on 2008-05-08
Hi ,
I have another alternative.

edit /etc/apache2/httpd.conf
add ServerName localhost

Then sudo apache2ctl restart.

It should do the trick ..

Tom

---

