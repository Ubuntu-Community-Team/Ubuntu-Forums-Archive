---
title: "Installed 6.06 but where can I find LAMP?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by ububob on 2007-04-30
I installed Xubuntu 6.06 and was successful in adding it as a 2nd OS to my old Win98 box. Now how do I find my webserver?

I want to run Apache so I can use this box as a web testing server on my home network.
How do I run this or should I have installed the server edition instead of the desktop version?

Do I need to download anything, or is it already on the ISO that I burned on the CD?

I'd also like to learn some Ruby on Rails and Python, so anyone have an idea how to do this? I'm very new and appreciate any advice regarding web development and learning how to run a webserver with Xubuntu.

thanks!

---

### Post by zetsumei on 2007-04-30
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

Just follow the download and install steps.  If you need any other help on it just reply back.

---

### Post by ububob on 2007-04-30
> **zetsumei said:**
> [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

Just follow the download and install steps.  If you need any other help on it just reply back.

I was told that I should do this elsewhere and not rely on the "prepackages" like xammp. Is there another way to install each at a time. (i'm also trying to learn so I can learn the process from an admin standpoint)

Thanks for the link though.

---

### Post by ZeroWing on 2007-04-30
> **ububob said:**
> I was told that I should do this elsewhere and not rely on the "prepackages" like xammp. Is there another way to install each at a time. (i'm also trying to learn so I can learn the process from an admin standpoint)

Thanks for the link though.

 I was told to use Windows, so.... :) 

 No, sorry. Can't help. You know, admins use prepackages, too.

---

### Post by zetsumei on 2007-04-30
You could install them via apt-get

```

sudo apt-get install apache2
sudo apt-get install mysql
sudo apt-get install proftp
and the packages that they need.

```

the reason i gave you the link to xampp was it has all you need, but you can try and look for some guides here that shows you how to install each one

---

### Post by ifthengoto on 2007-04-30
I found this useful

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by bobplano on 2007-04-30
> **ifthengoto said:**
> I found this useful

[https://help.ubuntu.com/community/ApacheMySQLPHP]("httphttps://help.ubuntu.com/community/ApacheMySQLPHP://")

the link to the site isn't quite right. you can't just click on it, you have to copy-paste. [here's]("https://help.ubuntu.com/community/ApacheMySQLPHP") a link if you don't want to do that though. you just put in the url wrong

---

### Post by ububob on 2007-04-30
zetsumei and ifthengoto,

those were what I was looking for...thanks bob for the link fix...!:KS :popcorn:

---

