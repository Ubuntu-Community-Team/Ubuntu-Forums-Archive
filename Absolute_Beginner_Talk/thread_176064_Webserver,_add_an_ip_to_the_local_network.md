---
title: "Webserver, add an ip to the local network"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by cje on 2006-05-14
I need to check out a few things before installing Ubuntu as a webserver.

Today, I'm running a SME server as local intranet server. Stable, but a litle bit late in updating the latest updates.

I would like to test out Ubuntu as a websert. But, I have a few importent feature I need to sort out first; 

1a) it it possible (or easy;)) to define that local network shall have free access to a folder - but password protected from all ip's outside of the local network? 
1b) if so, where do I set this preference for eathe folder?

2a) Is it easy to add an external IP as a part of the local network?
2b) is it possible to set this preference for each folder?
2c) if so, where do I set these preferences?

Thanks for all help!

---

### Post by souki on 2006-05-14
you can do anything with apache directives

go there [http://httpd.apache.org/docs/]("http://httpd.apache.org/docs/")
something like this :

```
 <Directory /var/www/secure>
  AuthType Basic
  AuthName intranet
  AuthUserFile /etc/apache2/passwd
  AuthGroupFile /etc/apache2/groups
  Require group Customers
  Order allow,deny
  Allow from 192.168.0
  Satisfy any
</Directory>
```

---

