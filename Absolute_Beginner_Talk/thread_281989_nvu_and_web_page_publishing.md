---
title: "nvu and web page publishing"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by bubbleblabs on 2006-10-21
I have installed nvu a web page package, i have set up my pc as an ubuntu server, i would like to publish my web page to the local host on my pc so i can check that it works with my database.  With nvu it seems to only let me publish to the web, i dont want to buy a domain name etc, because this is for practice, can anyone help..............?](*,)

---

### Post by mark2741 on 2006-10-22
I believe you'll need to setup a web server and deploy your web pages from that server. Most popular is Apache. I have no knowledge of Ubuntu Server so hopefully someone will provide better advice but certainly you'll need to put your pages in your web server. Then it's just a matter of making sure your web server is 'listening' (ie, running) and on what port and then just point to the localhosted pages with your browser.

NVU itself is not a web server.

---

### Post by Don Keeton on 2008-01-07
-Install apache2 package
-run apache2 in terminal
-type localhost in browser
An index should open 
Paste your html files in
/var/www

---

