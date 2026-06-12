---
title: "Apache2 blank configuration files"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by ZombieBear on 2007-04-27
I recently installed Apache2 on a ubuntu install, and everything ran fine, except I noticed that all my configuration files were fully blank. I can connect to my localhost and even accdes from other computers, but all it shows is the directory and all the files. It doesn't redirect me to index.html as it should, which puzzles me completely. I'm using PHP5 and MySQL, and running phpmyadmin and webmin as config tools. 
I can  access any document from the server without issues, but it always starts at the directory, not index.html.

---

### Post by az on 2007-04-27
In /etc/apache2/sites-available/ you have a default site.  It is configured to show you the directory (index) .  You can set the redirectmatch to point to any folder you want in the directory.  If you remoe the index directive, it should use the index.html

You can use and enable multiple sites.  Just copy the defaut in the sites-available directory to another name and then edit that file.  Then run

sudo a2ensite (name)
to enable that site.

---

