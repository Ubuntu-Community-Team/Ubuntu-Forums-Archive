---
title: "Ubuntu VMServer"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by lamagra on 2008-02-24
All,

I am currently in the process of building an Ubuntu LAMP stack box. I read around on a couple of ideas and was just wondering if someone could help clear some of my train of thought here. 

First of all the Ubuntu box I am building will have 4gigs of ram and probably a quad core (if i decide to go with the ubuntu vmserver idea) sitting in it. This will be primarily used for dev at home. 

Someone put the VMServer buzzword in my ear. 

What would be the purpose of installing VMServer and running some of my different applications (oracle, mysql, etc..) on different VM instances?

Why wouldnt I just go ahead and install it directly on ubuntu?

---

### Post by shanepardue on 2008-02-24
For server applications, there are some great reasons that can save you in the end. One 
of which could be...If you have a jabber chat server and a postfix email server on two 
separate vm instances and the mail server needs to be restarted after a kernel update, 
you don't have to kill your email for the reboot of the jabber server. This is just a small 
convenience, but there are others such as easy backups, separate settings, security 
policies, etc. If I hadn't said enough, they're fun!

---

