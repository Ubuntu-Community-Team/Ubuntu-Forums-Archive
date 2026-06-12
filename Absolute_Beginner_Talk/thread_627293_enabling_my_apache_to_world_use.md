---
title: "enabling my apache to world use"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by ronaldor9 on 2007-11-29
right now everying is working on my local network i got a couple of sites one for phpflux other for fun playing around and an ftp

my ftp works with the www    and it works from public pc

but my apache only works internally i got it all working on different ports with virutal hosts  but how do i enable world acces to a site

---

### Post by Ek0nomik on 2007-11-29
> **ronaldor9 said:**
> right now everying is working on my local network i got a couple of sites one for phpflux other for fun playing around and an ftp

my ftp works with the www    and it works from public pc

but my apache only works internally i got it all working on different ports with virutal hosts  but how do i enable world acces to a site

By default, an Apache install is open to the world unless you changed the HTTP port.  If you changed the HTTP port, you have to access the website via:  hxxp://www.yourwebsite.com:PortNumberHere.  (Ignore the x's).

Make sure you have the right port number when trying to connect in your web browser.  Otherwise you could post your conf file.  (I think it's in /etc/apache2/http.conf, but that's from memory, so I may be wrong)

---

### Post by ronaldor9 on 2007-11-30
yea thats the problem its not working online to the world only locally i mgiht have changed a setting here is my conf file apache2.conf

---

### Post by ronaldor9 on 2007-12-01
anyone

---

### Post by ronaldor9 on 2007-12-01
let me calarify some things my vhost website is on port 8080 then i got ports.conf to listen to port 80 and 8080

and my server name in apache.conf is localhost  ?? is this all correct

---

### Post by Dr Small on 2007-12-01
You could use this guide ( I wrote it ), to get the httpd on the web:
[http://php.8ez.com/drsmall/blog/?p=124](http://php.8ez.com/drsmall/blog/?p=124)

But it is for SSH, but same principles apply. Start at #6 for what you want.
And SSH runs on port 22, so you need to specifiy port 80 in all of those steps.

It is basically the same thing, just different service.

---

### Post by ronaldor9 on 2007-12-01
didint work   my site still is only viewable on local network

---

### Post by Dr Small on 2007-12-01
Did you open port 80 on your router (if you have one, and point it to your internal IP) and port 80 on your firewall ?

If so, then you should be able to access it via your external IP Address.

---

### Post by ronaldor9 on 2007-12-01
ive done every port forwarding im not sure whats wrong here is my vhost file 

NameVirtualHost *:8080

<VirtualHost *:8080>
ServerAdmin [email]webmaster@local.com[/email]
ServerName [www.jjohn.no-ip.org](www.jjohn.no-ip.org)
DocumentRoot /var/www/FTP-Shared/amohamad_public/
ServerAlias jjohn.no-ip.org *.jjohn.no-ip.org
</VirtualHost>

<VirtualHost *:8081>
ServerAdmin [email]webmaster@local.com[/email]
DocumentRoot /var/www/torrentflux/
ServerAlias johnflux.dyndns.org *.john.dyndns.org
</VirtualHost>

---

### Post by jflaker on 2007-12-01
> **Dr Small said:**
> Did you open port 80 on your router (if you have one, and point it to your internal IP) and port 80 on your firewall ?

If so, then you should be able to access it via your external IP Address.

You are correct.  Once the server is setup correctly, you must allow port 80 through your router.  Also, make sure that the PC hosting the Apache server has a static IP or you may lose access should your IP change in the future.

All requests come to your external IP address on port 80 and the router will forward the request on to the computer for service.

---

### Post by ronaldor9 on 2007-12-02
i mean when i type in my externall ip adress it works like the public one  it works
everything works
like this
[http://johnjohn.dyndns.org](http://johnjohn.dyndns.org)        WORKS
[http://www.johnjohn.dyndns.org](http://www.johnjohn.dyndns.org) DOES NOT WORK

###
my isp blocks port 80 or something becuse port 80 cannot be seen when i check it using an online method -->[http://www.canyouseeme.org/](http://www.canyouseeme.org/)  ###

what can i do

---

### Post by ronaldor9 on 2007-12-02
is this an issue i can work around?

---

