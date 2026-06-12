---
title: "Virtual hosts and document root(s)"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by HurricaneDan on 2007-04-30
I am trying to use virtual hosts to host two sites.  The first site works fine except which folder it reads from.

In my httpd.conf file I have this:

<VirtualHost 192.168.1.105:*>
ServerName [www.example1.org](www.example1.org)
ServerAlias example1.org
DocumentRoot /var/www/example1
</VirtualHost>

<VirtualHost 192.168.1.105:*>
ServerName [www.example2.org](www.example2.org)
ServerAlias example2.org
DocumentRoot /var/www/example2
</VirtualHost>

If I open my browser and look at [http://www.example.com](http://www.example.com) I get and index of / with a list of the directories and files from the /var/www directory.  How can I make sure it points to the correct directory?  And, how can I ensure that [www.example2.org](www.example2.org) is from the /var/www/example2 directory?

Thanks,

Dan

---

### Post by Pobega on 2007-04-30
From what I remember (I don't have Apache on this machine) there are two places where you define the document root; I've never bothered to get two websites working on one computer, but you may want to look through the configuration file to see if there is anything else you missed.

---

### Post by HurricaneDan on 2007-05-01
Pobega,

There was a second file and I had not changed it from the default.  Thanks for pointing me in the right direction.

---

### Post by mozmac on 2007-05-10
HurricaneDan,

What file was it that you found?  I'm trying to do the same thing you did.

---

