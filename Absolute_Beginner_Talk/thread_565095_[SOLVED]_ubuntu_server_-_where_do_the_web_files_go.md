---
title: "[SOLVED] ubuntu server - where do the web files go?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by thepiston on 2007-10-01
i wan to load a website to my server - where do they go?  i see the apache startup page, but i want to see my website.

---

### Post by llamakc on 2007-10-01
They go where you've told them to go. Look in /etc/apache2/sites-available for the default. On my machine that /etc/apache2/sites-available/default.

In that file look for DocumentRoot. Mine is /var/www.

---

### Post by gamerteck on 2007-10-01
By default, your web page files need to be located in: **/var/www/**.

---

