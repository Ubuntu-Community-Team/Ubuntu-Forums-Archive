---
title: "apache only to show website?"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-09-20
Can I install the ubuntu server and then just install apache so that I can play around with putting a website onto the web.

Or do I have to install the full LAMP stack.

I would like to just tackle one piece of LAMP at a time and add as i go along...

---

### Post by LotsOfPhil on 2006-09-20
Well, "just Apache" would be two parts of the LAMP since L stands for Linux. The Ubuntu server installs Linux, Apache, MySQL and PHP for you. Unless you are drastically short of disk space, you don't need to uninstall anything.

Just write your webpages in HTML and you'll only be using the apache part of the stack.

---

### Post by charles.g.moore on 2006-09-20
have you had any experience with webmin?
I really wanted to do this totally from the command line (im not sure my old system would be any good if I loaded the server GUI, but it seems all of the tutorials are mostly focused on using the webmin utility...

---

### Post by PriceChild on 2006-09-20
The server install on the alternate install cd installs ubuntu without a gui or any gui programs.

LAMP is an extra option for it which installs apache, mysql & php5 on top of the server install.

To install an apache server, simply type "sudo apt-get install apache2"

---

