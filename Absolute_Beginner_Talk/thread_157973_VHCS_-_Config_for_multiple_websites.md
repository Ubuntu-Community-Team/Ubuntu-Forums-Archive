---
title: "VHCS - Config for multiple websites"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by guysmiley on 2006-04-10
Hey all,

So I've done my best to read through the docs at vhcs.net and can't figure this out:

How do I config my system to host multiple sites using vhcs?  I have domain1.com, domain2.com, domain3.com...

Do I need to edit Apache directly?  If so, where?

How does the system know where to point a request to the server when there are multiple domains at 1 IP address?

Thanks for the help in advance!!!

gs

---

### Post by spanishwasabi on 2006-04-10
Sounds familiar :-P

I can tell you for Apache. There's something called Virtual Servers.
[http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html) (look for Name-based Virtual Hosts)
[http://plone.org/documentation/tutorial/plone-apache/virtualhost](http://plone.org/documentation/tutorial/plone-apache/virtualhost)
[http://www.petersblog.org/node/840](http://www.petersblog.org/node/840)

Simply create a file in /etc/apache2/sites-available/ with your given virtual host, and then put a link in /etc/apache2/sites-enabled/ (or use a2ensites or a command like that, look at the README in /etc/apache2/ ).

I'll not explain you again for the DNS, I think you got that part.

With VHCP? Simply have a look at the reseller interface (I think...) to add users (and thus domains), and then the user interface to create subdomains. Looks like it's pretty easy. You can train in their demo server.

Hope this time is clearer.

Enjoy!

G

---

### Post by spanishwasabi on 2006-04-10
Sounds familiar :-P

I can tell you for Apache. There's something called Virtual Servers.
[http://httpd.apache.org/docs/2.0/vhosts/name-based.html](http://httpd.apache.org/docs/2.0/vhosts/name-based.html) (look for Name-based Virtual Hosts)
[http://plone.org/documentation/tutorial/plone-apache/virtualhost](http://plone.org/documentation/tutorial/plone-apache/virtualhost)
[http://www.petersblog.org/node/840](http://www.petersblog.org/node/840)

Simply create a file in /etc/apache2/sites-available/ with your given virtual host, and then put a link in /etc/apache2/sites-enabled/ (or use a2ensites or a command like that, look at the README in /etc/apache2/ ).

I'll not explain you again for the DNS, I think you got that part.

With VHCP? Simply have a look at the reseller interface (I think...) to add users (and thus domains), and then the user interface to create subdomains. Looks like it's pretty easy. You can train in their demo server.

Hope this time is clearer.

Enjoy!

G

---

