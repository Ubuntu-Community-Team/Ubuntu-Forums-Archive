---
title: "Total Noob need simple web server"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by mandalay559 on 2007-02-27
Hello,

This is my first post.  I work for a city government and we are trying out Ubuntu on one of our PC's.

I dont know where to begin to start a web server.  What we have is a DSL Modem attactched to a live webcam.

We want this machine to be a webserver and have government employees to be able to access an address that will log them into the web cam to see the live video. It will ask for user name and password of course to access the live cam.

What do I need to download?  Can someone give me step by step instructions on what to download and how to set this up?  The cam is running off of a Netopia Modem.  It is for
survelliance purposes.

Apologize if this the wrong place to post.  We currently have Ubuntu 6.10 just been running on live cd first.

Any help would be appreciated.

Thanks for your time.

---

### Post by tronica on 2007-02-27
this should get you going with apache

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html")

---

### Post by christhemonkey on 2007-02-27
For a basic webserver as most people want, you should install apache2.

But for your needs, i dont know what to suggest?
What sort of cam is it? (make model etc)
and what sort of modem? (model of netopia)

---

### Post by rjfioravanti on 2007-02-27
Apache is the web server people usually go with, you can download that from the ubuntu repositories

sudo apt-get install apache2

not sure what you are going to do about your video cam, I suppose the first step is to install the website, get your user authentication going and then worry about hooking up the camera to your website

you are probably going to need php5 as well if you want user authentication happening

you can see this [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_PHP5](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_PHP5)

---

### Post by tronica on 2007-02-27
there is a app called webcamd, with grabs images from a cam, and uploads them to apache, would that work.

---

### Post by proalan on 2007-02-27
Theres a package called lamp (aka xampp) that includes the latest apache and mysql builds

easy to use and customise (customize if your american)

---

