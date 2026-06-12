---
title: "PHP in Ubuntu"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by twp_twm on 2008-04-03
I have installed PHP5 and have made an html page with a .php extension so could someone tell me how and where i should save it (the path) and, also the code how to call it please

---

### Post by Cypher on 2008-04-03
You have two options..
1) Place all files in the /var/www/apache2 directory which is the default directory with Root privileges
2) Enable the UserDir module with (sudo ae2enable userdir && sudo /etc/init.d/apache2 restart) and then create a directory called "public_html" in your home directory. Place the file (index.php) in that directory and access it by pointing your browser to http://localhost/~<username>

---

