---
title: "Website building - mysql"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by niceguy123 on 2007-09-05
I'm new here and am not sure which category would be best to post this in so I'll start here.

I have successfully installed XAMPP and am now trying to run a website that I built online (in Joomla) I have downloaded the site folders to localhost and backed-up mysgl db with the site's cpanel, but I can't figure out where and how to import it to mysql on this computer.

Any help would be greatly appreciated. 

Thanks

---

### Post by KCPokes on 2007-09-05
You can do it commandline, using mysql commands, but if you are relatively new to it you might just consider downloading the webmin package (webmin.com).  It has a GUI configuration, under servers, that allows you to create, administer, etc... databases.

---

### Post by niceguy123 on 2007-09-07
> **KCPokes said:**
> You can do it commandline, using mysql commands, but if you are relatively new to it you might just consider downloading the webmin package (webmin.com).  It has a GUI configuration, under servers, that allows you to create, administer, etc... databases.

Yes, I am new. Is the commandline and terminal the same? Where can I find a list  of the commands I would be using?

---

### Post by JohnCub on 2007-09-07
command line and terminal are the same.

for your purposes, importing data, you'll use a command similar to:
mysql {databasename} < {filename.sql} -u{joomlas username} -p{joomlas password}
(don't use the { or } )
The mysql website is excellent for documentation and it's almost human readable.  :P

---

### Post by alan4573 on 2007-09-07
> **JohnCub said:**
> and it's almost human readable.  :P

:lolflag:

---

### Post by frrobert on 2007-09-07
Xampp includes phpmyadmin.  It is a web based graphical interface for creating and manipulating mysql databases.  In fact in may be the interface you used to download your existing database.  Phpmyadmin  is listed under tools on the xampp startup screen.  Hope this helps.  

Don't forget to change your configuration file on your local copy of joomla so it points to the local database.

---

