---
title: "Hosting sites"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Rhaddad on 2007-07-04
Hey,
I have installed ubuntu server 7.04, but i am completely clueless on how to host a website using it. I understand that i need DNS name servers. Which i have. But not sure how to host.

Thank you

---

### Post by scxtt on 2007-07-04
you need apache2 to be installed, then you can use something like dyndns.org to forward a named URL to your WAN IP ... or you can pay some amount of $$$ to have more control over the sites name ...

---

### Post by Rhaddad on 2007-07-04
I understand that bit. But not were to save the files and set it up in the server

---

### Post by scxtt on 2007-07-04
put your site's files in **/var/www** {unless /etc/apache2/apache2.conf points somewhere else} and make sure www-data:www-data owns them and that they are "world readable" ... then point your browser to your WAN IP or DNS name ... if you're behind a router, forward port 80 to the LAN IP for the apache2 host ...

---

### Post by hyper_ch on 2007-07-04
Have a look at the howto at [http://www.howtoforge.com](http://www.howtoforge.com)

---

