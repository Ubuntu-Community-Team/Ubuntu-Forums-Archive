---
title: "Apache | Permissions Disorder"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Srirangan on 2007-02-03
Ok .. so I installed Apache and PHP and MySQL. 

Now.. I try to create a file in default apache document root : Not allowed

Then.. I try changing the document root : Not allowed

Boom .. I'm stumped..

So I searched this forum, and I read that I have to set the perms using sudo .. What is sudo? How do I use it? :confused:

---

### Post by Srirangan on 2007-02-03
Bump. :(

---

### Post by Srirangan on 2007-02-03
Fixed with: sudo chown "username" /var/www && sudo chown "username" /etc/apache2

---

