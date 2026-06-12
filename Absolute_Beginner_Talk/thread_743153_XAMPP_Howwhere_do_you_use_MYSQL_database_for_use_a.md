---
title: "XAMPP: How/where do you use MYSQL database for use access?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-04-02
I've successfully installed XAMPP. I've successfully gone to my localhost and also done port forward to be able to access from the internet. 

I've also successfully added a user and password, so that when you access /IPaddy/user, it will ask for a user and password. This was done in the httpd.conf file. 

What I don't understand is how the sql database comes into play. I see questions on adding users to the database and such. Does this also control user access? 

Can someone point me to info on this subject?

---

### Post by BlizzofOZ on 2008-04-02
Still searching...  bump

---

### Post by louieb on 2008-04-02
XAMPP and internet really don't mix (security risk above a normal lamp install). MYSQL is just the database component of LAMP it does whatever you tell it to do. For documentation the mysql.org website is your best bet.
But heres a couple of Ubuntu and LAMP links to checkout.
  [HOWTO: (XAMPP) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=223410")
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by BlizzofOZ on 2008-04-02
> **louieb said:**
> XAMPP and internet really don't mix (security risk above a normal lamp install). MYSQL is just the database component of LAMP it does whatever you tell it to do. For documentation the mysql.org website is your best bet.
But heres a couple of Ubuntu and LAMP links to checkout.
  [HOWTO: (XAMPP) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=223410")
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Thanks and I understand that...

I'm looking to turn it and off as needed.  I want to be able to allow particular users to have access, but I won't have it on all the time.  I won't be doing any web serving all the time.

There is a way to be able to create a user database, with passwords, that thru PHP, XAMPP can ask for user/password login.  It that added security measure that I'm looking for and what you hit upon.

I just can't find a "How To" guide on how to do this...

---

### Post by louieb on 2008-04-02
There are a couple of  packages you can install one is **phpmyadmin** for managing mysql. Its in the repositories but may not work for an  XAMPP install out of the box. Works with a normal LAMP install out of the box.

The other is [Webmin]("http://www.webmin.com/")  for administration of all kinds of servers its not in the repositories but not all that hard to install. 
[Webmin on Dapper Server - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=195093")
[Installing Webmin On Ubuntu Feisty Fawn (7.04) | HowtoForge - Linux Howtos and Tutorials]("http://www.howtoforge.com/installing_webmin_ubuntu_feisty")

---

