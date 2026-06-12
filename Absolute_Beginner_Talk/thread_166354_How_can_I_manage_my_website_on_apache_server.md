---
title: "How can I manage my website on apache server?"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-26
Hi .. I have just installed apache, mysql, php and phpmyadmin.
everything is fine, and localhost is working ... but I dunno yet where are the server files so I can manage my website's files.

Any help will be appriciated.

---

### Post by jazzmuzik on 2006-04-26
Try this on the command line:

more /etc/apache2/sites-available/default

Look for the DocumentRoot setting. This is the main directory for your html (php,etc) pages.

Also, all your users can create web pages in their home accounts. Just create a directory called "public_html" like /home/joe/public_html. Add an html file and test it: surf to [http://localhost/~joe/myfile.html](http://localhost/~joe/myfile.html)

---

### Post by Isoss on 2006-04-28
Thanks, everything works fine now.

---

### Post by Isoss on 2006-05-01
OK ... now I am not able to manage my DB ... in phpmyadmin I can't insert any new record or update or delete anything ... what can I do ? it looks like read only ... I need a write perission ... please help ... 

how can I get a write permission to the /var/www/ folder as well? 

Thanks ...

---

### Post by Bagnaj97 on 2006-05-01
[QUOTE=Isoss]OK ... now I am not able to manage my DB ... in phpmyadmin I can't insert any new record or update or delete anything ... what can I do ? it looks like read only ... I need a write perission ... please help ... 

how can I get a write permission to the /var/www/ folder as well? 

Thanks ...[/QUOTE]

You can use sudo before your commands for permissions in /var/www or if you want to do things graphically then try sudo nautilus /var/www/

As for managing your database install mysql-admin either using synaptic or ```
sudo apt-get install mysql-admin
```. Once you have it installed just run mysql-admin. To start with use the user name root and no password, the server should be localhost.

---

