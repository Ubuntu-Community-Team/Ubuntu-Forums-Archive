---
title: "[SOLVED] trouble finding ssl certs"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by DaveyG on 2007-03-27
After having trouble earlyer installing Apache-ssl i finaly got it working with help from a few kind people of the forum..

My trouble now is that i cant find were the ssl certs are stored.. iv done a search for *.key and *.cert but had no luck, could anyone be of any assistance?

Any help is much appreciated.

Thanks, Davey

---

### Post by DaveyG on 2007-03-27
Bump...

---

### Post by DaveyG on 2007-03-27
Bump...

---

### Post by DaveyG on 2007-03-27
Bump...

---

### Post by DaveyG on 2007-03-27
Bump...

---

### Post by zebog13 on 2008-02-28
if you do sudo aptitude install ssl-cert openssl  that should get you started. However, setting it up with apache2 is killing me

---

### Post by atgheb on 2008-02-28
perhaps you need to run updatedb first.
simple type 
```

updatedb
locate *.cert
locate *.key

```

Also, the ssl certificate might be in *.pem format which you'll need to convert to the crt and key formats.
In which case there are great directions on this site:
[http://www.akadia.com/services/ssh_test_certificate.html](http://www.akadia.com/services/ssh_test_certificate.html)

---

### Post by zebog13 on 2008-03-05
actually, I figured it out..
using php5, apache2, in the httpd.conf on the top,add NameVirtualHost *:443

then do someething to this matter

<VirtualHost *:80>
        ServerName servername
        DocumentRoot /var/www
</VirtualHost>

<VirtualHost *:443>
        ServerName servername
        DocumentRoot /var/www

        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.pem
</VirtualHost>

Then apache2ctl that bad boy
:popcorn:

---

