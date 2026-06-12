---
title: "httpd.conf"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Sout on 2007-08-21
O am really confused now :confused: I am trying to get my web page up and running :confused: 

Where do you you have to change apache to point to your site? Httpd.conf is of no help .... tried apache2.conf ... I am going in circles here ... 

I am not asking how to do it ;) Just to point me to the correct file .... please :lolflag:

---

### Post by Dr Small on 2007-08-21
What exactly are you wishing to fulfil?

---

### Post by LaRoza on 2007-08-21
> **Sout said:**
> O am really confused now :confused: I am trying to get my web page up and running :confused: 

Where do you you have to change apache to point to your site? Httpd.conf is of no help .... tried apache2.conf ... I am going in circles here ... 

I am not asking how to do it ;) Just to point me to the correct file .... please :lolflag:

If you are using Ubuntu, put the site in /var/www

So, if you have /var/www/index.php, you will just have to browse to: [http://127.0.0.1/index.php](http://127.0.0.1/index.php), if this is a localhost.

The domain name will point to the root of that directory, and serve files named index.php, index.htm, index.php5, and a few others, by default.

---

### Post by Dr Small on 2007-08-21
I find it simpler to install XAMPP from [url=http://apachefriends.org]ApacheFriends[/urk], and I have done that 3 times and set up a localhost every time with success. It is very simple.

Dr Small

---

