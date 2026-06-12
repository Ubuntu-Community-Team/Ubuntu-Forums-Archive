---
title: "webmin"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by psychobeauty on 2008-03-25
hello..


can anyone give me a hind on how Webmin works???
i want to configure apache...any thoughts????

---

### Post by kellemes on 2008-03-25
- Visit [the download page]("http://www.webmin.com/download.html") to download the ubuntu deb-file..
- Install like so.. "sudo dpkg -i webmin_1.400_all.deb"
  If you get messages about libraries missing etc.. just do the following.. "sudo apt-get -f install"
- Open you browser and visit "https://localhost:10000/"

---

### Post by psychobeauty on 2008-03-25
thanks for the reply....


but i ve done everything...the problem is that i dont know how to use webmin..... how to setup the apache webserver from there....


can u help??

---

### Post by kellemes on 2008-03-25
I assume you have apache installed?
If not just do..
```
sudo apt-get install apache2
```
The Webmin Apache-module needs a working apache-setup..

A lot more info on setting up an Apache (LAMP) server with Ubuntu.
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by psychobeauty on 2008-03-25
I have apache install..now??

---

### Post by psychobeauty on 2008-03-25
how do i set up apache webserver from webmin

---

### Post by kellemes on 2008-03-25
What's [http://localhost](http://localhost) showing?
If it's showing anything you have Apache setup.

What do you want to do with Apache? Is there anything in particular you need? I mean, you can setup Apache in a million ways so it really depends on your wishes..

---

### Post by psychobeauty on 2008-03-25
in localhost it open a page says it works..so everything its ok..

i want to setup a web server to access my file throught the internet....


:) thanx for helping me

---

