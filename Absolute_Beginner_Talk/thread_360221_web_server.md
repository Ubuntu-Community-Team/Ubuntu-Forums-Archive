---
title: "web server"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by specbailey on 2007-02-12
I want to use my linux (Ubuntu) machine to also be a web server.  How do I go about doing that?  I was looking at the Apache web server, is that the best to use, and how do I set everything up?

---

### Post by etank on 2007-02-12
To just get apache on the machine you can do ```
sudo aptitude install apache2
```Or you can click System->Administration->Synaptic and do a search for all apps that have apache2 in the name. Apache is a very good web server.

---

### Post by specbailey on 2007-02-13
OK, I downloaded Apache.  How do I go about using it.  It doesn't show up in my taskbar applications.  Do I need to run it by command?

---

### Post by Bachstelze on 2007-02-13
Just put your HTML files in /var/www, open your favourite web brower and type [http://127.0.0.1](http://127.0.0.1) :)

---

### Post by HomerSimpson748 on 2007-02-13
I been using [xampp]("http://www.apachefriends.org/en/xampp.html"). There are tons of tutorials out there that can walk you through securing it for www use.

---

### Post by specbailey on 2007-02-13
is there any risk of security problems, or internet connections problems?

---

### Post by nhandler on 2007-02-13
You can also access it by going to 'localhost' without the quotes. The configuration is in /etc/apache2/apache2.conf.
I've been using apache for a while now. Unless you are planning on running a server for a big company or high traffic website, you shouldn't even be able to tell it is running. By that, I mean there should be no slow down of your computer. Security could be a problem. The server itself is secure. However, depending on what you plant to use it for, YOU might make it insecure. But that would be the same for any server. Just be careful.

---

### Post by specbailey on 2007-02-14
So if I have a website already being served, but want to put it on my apache server, how do I do that.  Do I need to do anything special like a static IP address?  How do I change over from one server to this one?

---

### Post by sumguy231 on 2007-02-14
> **specbailey said:**
> So if I have a website already being served, but want to put it on my apache server, how do I do that.  ... How do I change over from one server to this one?

If you want to move the pages from the old server, you need to put the pages you want to serve in /var/www. Note that by default, it will redirect to a default page which you may have to change in /etc/apache2/sites-available/default. 
If this happens, edit that file and put a # in front of the line that says:
```
RedirectMatch ^/$ /apache2-default/
```

> Do I need to do anything special like a static IP address? 
If you want to set a hostname for your server, you'll probably want a static IP address, yes.

P.S. If you're running this on a home connection, you should check your ISP's terms of service - a lot of them don't like you running a web server which will receive a lot of traffic and may suspend your account/get you to buy a business account.

---

