---
title: "web server help... I dont know were to start..."
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by speedingbullet on 2007-01-14
My operating system is Xubuntu edgy. Why I am doing this is because Ive gotten fed up with looking for free web hosts that are php and other web-language compatible. So I've decided I want to set up my own web server. The problem is, I barely know what I'm doing... Ive installed apache.... but what now? Their little guide is confusing. I don't want to pay for a domain name, so I'm going to use co.nr's free url redirection service....  but I'm very lost.... what should I do next?

---

### Post by izua2 on 2007-01-14
Well, you can try [Xampp]("http://www.apachefriends.org/en/xampp.html").
It combines apache, php and mysql in an easy to install .. erm.. archive. it's not the real thing, most like a development environment, but hey, with a little effort it can be secured up to work as a real web server.

---

### Post by justin_c18 on 2007-01-14
When I had a server going I installed from the dapper server cd, of course no gui. But, you can

```
sudo apt-get install xubuntu-desktop
```

so you have a GUI to go by, then update

```
sudo apt-get update
```

LAMP server consists of Linux Apache MySQL, and PHP. It's a very good setup. Really Solid. Depending on your ISP, you have to forward port 80 on your router. and give your machine a static IP if you don't have one. 
[http://www.no-ip.org](http://www.no-ip.org) has a good setup for a redirection type of thing. There's also a no-ip package in one of the repositories regarding an update client if you have a dynamic external IP(always changes). 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

That page has a really good reference. It will tell you how to install everything correctly, and get it working good.

Cheers,
Justin :-D

---

