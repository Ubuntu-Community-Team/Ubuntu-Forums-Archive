---
title: "Multiple web sites for development"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by HeavyEddie on 2006-09-06
I've successfully installed PHP, Apache and MySQL on my system for development purposes.  Works great!  I'm new to Linux, but am having a blast so far :)

Anyway, I'm using [http://localhost](http://localhost) to test my website locally.  Thing is, I have several sites that I would like to do the same thing for.  The question is how do I install them in different directories and once I've done that... what would I use for a URL?

Thanks for any help in advance.

---

### Post by Unflux on 2006-09-06
I cant remember the ins and outs of Apache since I`m to lazy to install it and just upload to a test directory on my live server but as far as I can remember there is a folder where you need to save all PHP/HTML files.

All you do is create a folder structure there and call it in the address bar [ I.E. [http://localhost/folder1/index.php](http://localhost/folder1/index.php) or [http://localhost/folder2](http://localhost/folder2) etc ].

---

### Post by indytim on 2006-09-06
Why don't you put each one of your test sites within a specific folder within /www?  Remember $DOCUMENT_ROOT is your friend.:) 

IndyTim

---

### Post by Uluen on 2006-09-06
Use Apache vhosts and update /etc/hosts to reflect the various sites like this:
ip-of-your-machine  test1.blah.com
ip-of-your-machine  test3.blah.net
ip-of-your-machine  test.blargh.org

---

### Post by HeavyEddie on 2006-09-06
Thanks everyone... I'm reading up on vhosts right now.

---

### Post by HeavyEddie on 2006-09-07
OK, is there a repo for vhost or will I need to make it per [the instructions]("http://chaogic.com/vhost/documentation#start_install").

---

### Post by HeavyEddie on 2006-09-07
double post

---

