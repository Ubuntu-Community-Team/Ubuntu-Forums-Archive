---
title: "server install"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-09-15
Quick question. When installing ubuntu I noticed the server install option and was wondering if that will automatically set up apache2 for me? I set up apache on my machine now but am currently building my own computer with 64 bit chipsets so soon I will install ubuntu 64 bit on it. If I only plan to use it as a small webserver and pc should I go with a server install or will that be too much?

---

### Post by az on 2006-09-15
> **emprog said:**
> Quick question. When installing ubuntu I noticed the server install option and was wondering if that will automatically set up apache2 for me?

No.  See here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

will install the lamp stack.

All you get with a "server" install is a barebones linux system.  You get the command line and the basic unix tools.  Less is more - a production server should not be running stuff that it does not need to be.  Hence the server install is just a really basic system.

> **emprog said:**
> 
 I set up apache on my machine now but am currently building my own computer with 64 bit chipsets so soon I will install ubuntu 64 bit on it. If I only plan to use it as a small webserver and pc should I go with a server install or will that be too much?

What do you want to serve?  If you want to host one LAMP-powered website, a pentium one with 64 megs of ram would do the trick.

If you want to host a few hundred sites at the same time, yeah, a 64-bit machine will run faster.

---

### Post by emprog on 2006-09-15
Thanks for the reply. Actually, I am starting to get into programming with SDL/OpenGL and read about AMD chips being good for gaming apps. I also got a nice price for my AMD64 3700+ 939 socket for 100 dollars delivered to my door. But anyways, I just host my own personal site with apache so it's nothing serious at the moment. I mostly work with programming in Java/C++, and utilizing multimedia libraries like SDL + OpenGL. This is the main reason I will be using my computer but was curious at what the server offered but I guess it's best to stick with the default installation if my webserver is just to host a simple site right?

---

### Post by clarkth on 2006-09-16
another option that it looks like a lot of people do is to do the server install then add fluxbox on top.

---

