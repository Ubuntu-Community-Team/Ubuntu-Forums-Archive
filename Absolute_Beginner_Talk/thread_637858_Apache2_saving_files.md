---
title: "Apache2: saving files"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by gleble on 2007-12-11
I have successfully installed Apache2 and I gather that uploaded files go in sites-available or maybe sites-enabled but when I try to save a file I get:

 Could not save the file /etc/apache2/sites-enabled/first.htm

It says I haven't got permission so I look in httpd.conf and there is nothing there. Using Ubuntu what should be there?

---

### Post by MossKiller on 2007-12-11
Your HTML files should be going in /var/www/.

You don't need anything in your httpd.conf - configuration is done in /etc/apache2/apache2.conf and /etc/apache2/sites-available/default - but you can put some configurations in there.

---

### Post by mcduck on 2007-12-11
Actually the correct place is /var/www.

To put files there (from the same machine) you can run 'gksudo nautilus' to open the file manager as root. Then go to File/New Window to open another window, as both source and destination windows need to be running with root privileges.

If it's a development machine there's easy way how you can just drop the files into a directory inside your own home dir: just link a directory in your home into a dir inside /var/www. For example, 'sudo ln -s /home/mcduck/Public /var/www/mcduck' will create a link from the Public directory in my home to correct place, I can just drop files into that directory and access them with the address 'localhost/mcduck' though the browser.

---

### Post by gleble on 2007-12-11
Thanks that's sorted out .htm files which are opening nicely in localhost. However alot of my files are .php in that they are .htm but contain the line <?php include"headandnav"; ?>
Ubuntu wants to open them in a word editor. How do I get them to parse.

---

### Post by mcduck on 2007-12-11
Have you actually installed PHP? It's a separate package from Apache..

---

### Post by gleble on 2007-12-14
Correct, silly me forgot it was my server, assumed it was there

---

