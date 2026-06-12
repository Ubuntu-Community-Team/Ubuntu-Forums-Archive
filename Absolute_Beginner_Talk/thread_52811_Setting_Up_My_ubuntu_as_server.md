---
title: "Setting Up My ubuntu as server"
date: 2005-07-29
forum: Absolute Beginner Talk
---

### Post by vanong on 2005-07-29
Does anyone knows a link/documentation guide on how to settup ubuntu as a server? (file,Dns,Web) 

Also does ubunto (if set-up as a server) can modify other ubuntu workstation is working environement? (Like MS sever does) 

Thanks!

---

### Post by heimo on 2005-07-29
[QUOTE=vanong]Does anyone knows a link/documentation guide on how to settup ubuntu as a server? (file,Dns,Web) 
[/QUOTE]

I can't give specific instructions, but it'll be easier for you to search for software specific information. For Windows compatible file server software, samba is the one you want to try, other possibilities nfs, ftp (vsftpd). For DNS, the grand old man is BIND (bind9) and for web server Apache is the one you want to know (apache2).

Those are not in anyway Ubuntu specific - if you know how to install and configure one on Ubuntu, you know how to do it in Debian, Fedora, Redhat and Gentoo. Best detailed information is on the websites and manual pages. For example, [www.apache.org](www.apache.org)

For some of these, you'll get help searching this forum. If you're unfamiliar with setting up Linux server, you definitely want to check webmin (web based configuration tool for many different server software). Apache is quite easy to setup in Ubuntu, Samba is probably a bit harder and Bind is definitely the most confusing if you're unfamiliar with the network jargon.

If you can't get started, can't find some information you're looking for, or I didn't answer your question, please do not hesitate to ask more detailed questions. :)

---

### Post by Wide on 2005-07-29
I really dont know anything about microsoft products but you can get a start in the Ubunto guide found [here](http://ubuntuguide.org/#apachehttpserver)


Hope this helps :grin:

---

### Post by Kvark on 2005-07-29
To set up a web server, just install the packages you want from synaptic (for example apache2, php4 stuff, mysql stuff). It all works directly after you install without any configuration needed.

But I bet you will still want to fine tune the configurations. To set up user accounts for mysql, turn off error reporting for apache, performerance tweaking and custimize behaviour, etc.

Don't know about server programs for other purposes but synaptic is probably place to start for that too.

---

### Post by heimo on 2005-07-29
**HOW TO : Create a FTP server with user access (proftpd)**
[http://ubuntuforums.org/showthread.php?t=51611]("http://ubuntuforums.org/showthread.php?t=51611")

---

