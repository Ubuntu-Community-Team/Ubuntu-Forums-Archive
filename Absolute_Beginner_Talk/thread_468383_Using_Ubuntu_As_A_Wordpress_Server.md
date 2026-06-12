---
title: "Using Ubuntu As A Wordpress Server?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-06-08
I would like to set up a Wordpress server, but I don't have any money. I do have a 5 year old desktop computer that runs Ubuntu. I know how to install Wordpress and make it a local server, but how can I go about getting it on the World Wide Web.

---

### Post by Limpan on 2007-06-08
The first thing you need to know is if you have a static IP or a dynamic?

One common thing you have to do is to make sure that port 80 is reachable from the outside. This can be done in several ways. If the server has a public address then you're good to go. Otherwise you'll need to route the traffic between the internet and your server.

If you don't have a static IP you'll need something like dyndns.org that can help people find you (with a human readable address that is).

---

### Post by az on 2007-06-08
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

---

### Post by tdrusk on 2007-06-08
Thank you both.

---

### Post by tdrusk on 2007-06-10
I am at this part.
> Alternatively

There is more than just one way to set the mysql root password and create a database. For example mysqladmin can be used:

mysqladmin -u root -p password yourpassword

and

mysqladmin -u root -p create database1

mysqladmin is a command-line tool provided by the default LAMP install. 
I am kind of confused on what to enter. Let's say I want  my password for mysql to be "chicken". Would I do
mysqladmin -u root -p password chicken
?

It keeps telling me 
> mysqladmin: connect to server at 'localhost' failed.
error: 'Access denied for user 'tyler'@localhost' (using password: YES)'
Any help is very appreciated.

---

### Post by Limpan on 2007-06-12
> **fuzzyhair said:**
> 
I am kind of confused on what to enter. Let's say I want  my password for mysql to be "chicken". Would I do
mysqladmin -u root -p password chicken

Yes. That's what they mean.

The problem then is either that the MySQL daemon isn't started or that you do not provide a correct username. It says that you tried to login as _tyler_ on localhost. Have you created that user?
Try this:
```
mysql -u root --password
```
which should then ask you for the password you entered previously (chicken).

---

