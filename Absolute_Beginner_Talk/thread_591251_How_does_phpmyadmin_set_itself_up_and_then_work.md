---
title: "How does phpmyadmin set itself up and then work?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by maudmoonshine on 2007-10-25
This is probably a really stupid question...
 
I have apache2 set up with one (can you have more than 1 at a time?) 'virtual server' that points to a directory I choose. Apache2 runs as a local server (127.0.1.1 if I recall).
 
I connect to my apache 'virtual server' from a machine on my local network (say 192.168.0.4) by entering [http://192.168.0.50/](http://192.168.0.50/) (that's what I've fixed my router to know this particular server as) and I get a directory listing or index.html executed (whatever); if I specify directories that exist below this then I get their listing or whatever. Just as I'd expect, although 'vurtual servers' are new to me.
 
Entering [http://192.168.0.50/phpmyadmin/](http://192.168.0.50/phpmyadmin/) gets me phpmyadmin's log-on page.
 
But how and why?
 
I don't have a 'virtual server' set up for this (and neither does phpmyadmin?) and /phpmyadmin/ is not on the directory tree of the 'virtual server' (my site) that I do have set up (its at /usr/share/phpmyadm as far as I can tell).
 
How come it works?

---

### Post by LaRoza on 2007-10-25
Look in the configuration files for Apache, it should be there.

---

### Post by reckless2k2 on 2007-10-25
LaRoza is right. if you look in the /etc/apache2 tree you can navigate to a phpmyadmin config file that will explain the symlink in /var/www that enables the pointer using the url. 

BANG!!!

mark it as SOLVED...mark it as SOLVED!!

---

### Post by maudmoonshine on 2007-10-25
If you say so :-)))
 
I have a lot to learn.
 
I've found etc/apache2/conf.d/phpmyadmin.conf which is likely what you mean.
 
But I don't understand at the moment; but I will eventually...

---

### Post by reckless2k2 on 2007-10-26
the file in conf.d basically tells apache to be able to open [http://yourserver/phpmyadmin](http://yourserver/phpmyadmin). the file is well commented so it should be easy to understand. there's a piece in the apache2.conf file that says to look there to add/load anything else. i think webalizer appears here as well if and when you set that up.

---

