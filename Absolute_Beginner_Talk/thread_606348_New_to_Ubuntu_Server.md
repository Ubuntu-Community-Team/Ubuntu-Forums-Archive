---
title: "New to Ubuntu Server"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by kmac on 2007-11-07
Not new to Linux nor Ubuntu, mind you. I've just received a desktop to be used as a dedicated webserver and i started out lost right from the get-go. I'm not intimidated by text-only, but I sort of was expecting some sort of GUI. I would just like some advice on configuring my server to run as a  web and local sever and how to set up ssh and mail accounts and whatnot.

Any help would be most appreciated.

--Kyle

---

### Post by Dr Small on 2007-11-07
I have no idea about mail accounts, as I have never done it, or been successful at it, but to setup a SSH server, run:
```
sudo apt-get install openssh-server
```

I would suggest Webmin, as a web-based GUI for managing your server. I have it on this machine, and it is awesome (although this is not a server, but it would work good on one).
[http://www.webmin.com/](http://www.webmin.com/)

Dr Small

---

### Post by MrFSL on 2007-11-07
Hello Batavia! - Been a long time since I was down that way --

A web server is not that difficult but mail can be problematic.

For a web server you will want to use Apache web server:```
sudo apt-get install apache2
```

It is relatively easy to configure. Configuration files are found in: /etc/apache2

If you are interested in setting up a simple site the only file that need be altered is httpd.conf

A wealth of information can be found at: [http://httpd.apache.org](http://httpd.apache.org)

---

### Post by kmac on 2007-11-07
Thanks a lot.

Why have you been in Batavia? From Alaska?

--Kyle

---

### Post by Dr Small on 2007-11-07
Also, 
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96) -- Apache, The Easy Way (with php-gd2 support)
[http://php.8ez.com/drsmall/blog/?p=124](http://php.8ez.com/drsmall/blog/?p=124) -- Setup a SSH Server

---

