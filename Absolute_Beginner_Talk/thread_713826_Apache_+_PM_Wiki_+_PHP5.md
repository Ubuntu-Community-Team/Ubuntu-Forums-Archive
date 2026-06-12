---
title: "Apache + PM Wiki + PHP5"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by psylance on 2008-03-03
Wanna try out hosting a wiki of my own.

Had a few question at the moment.

Installed the wiki in /var/www/pmwiki/.

Now to access the wiki, i need to go to [www.mydomain.com/pmwiki/pmwiki.php](www.mydomain.com/pmwiki/pmwiki.php).

how can i simplify the way of accessing it?

I wanna access it by going to [http://wiki.mydomain.com](http://wiki.mydomain.com)

How do i configure the redirects?

---

### Post by psylance on 2008-03-03
The best i can do was : 

[http://www.mydomain.com/pmwiki](http://www.mydomain.com/pmwiki)

---

### Post by araz on 2008-03-03
You may create an alias to do that.

here is an example:

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

Hope it helps :)

---

