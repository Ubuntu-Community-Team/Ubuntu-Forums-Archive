---
title: "Web server setup question"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by NoBullMan on 2005-11-24
Hi,
I have installed Ubuntu and want to make the PC into a web server. I am not sure if Apache is part of Ubuntu or if I have to download and install it manually.
Can you guys tell me what I need (to do) to set up my PC into a web server?

How about PHP and MySQL? Do they need to be setup separately? If so, how?

What I want to do is to set up a Linux web server on my network (Windows) and host a few sites before doing it for real. (I guess I have to give my PC a static IP on local network)

Thanx.

---

### Post by Jonne on 2005-11-24
Open synaptic, enter your password and you'll find an interface that allows you to install the packages you need automatically. You'll need to search for apache (or apache 2, i think you can choose), php and mysql.

To install phpmyadmin (one way to administer your MySQL server), you'll have to get it from the [site](http://www.phpmyadmin.net/), I think.

It couldn't be easier.

It wouldn't surprise me if there was already a guide in the wiki, or a HOWTO in the forums.

---

### Post by NoBullMan on 2005-11-24
Thanks for the reply. I checked the wiki and found a page for setting up Apache, PHP and MySQL:
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

