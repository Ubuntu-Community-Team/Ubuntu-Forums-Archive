---
title: "Apache2 Firefox PHP"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by ladycard on 2008-01-10
Hello,
I have apache2 working and it will pick up the html but when it comes to the php firefox is not loading the page correctly.

When I run [http://localhost/testphp.php](http://localhost/testphp.php) I get a popup in firefox saying php is a script and do I want to open it . When I click open with firefox and click okay the page keeps loading a bunch of blank untitled webpages. I have gone through the the httpd.conf, apache2.conf and the php.ini files and they all look okay. Is there another file I need to check for configurations. This is the first time I have encountered this problem. I have set apache2, php and firefox up in windows xp and in slackware without having any problems.

Thanks! 
Barb

---

### Post by LaRoza on 2008-01-10
How did you install Apache? You have to install the PHP modules too.

It is not a firefox problem, Apache isn't running the script.

---

### Post by angels on 2008-01-10
I had the same problem...but it was solved on its own as soon as I installed everything - SQL, PHP and Apache2. 
However, I asked at the ubuntu mailing list as well :)
and you can check here (mentioned as LAMP) [https://lists.ubuntu.com/archives/ubuntu-users/2007-November/129329.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-November/129329.html) 

you can go at
[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100)
there is a good guide on installing LAMP on ubuntu 7.10

Cheers,:KS
Angels

---

### Post by timbounceback on 2008-01-10
are you sure you have everything installed?
sudo apt-get install php5

---

### Post by ladycard on 2008-01-11
Thanks for the suggestions!  I did end up reinstalling Apache2, PHP5 and Mysql. Everything seems to be working fine. :)

ladycard

---

### Post by DanielDutton on 2008-02-25
A reinstallation of libapache2-mod-php5 using Synaptic Package Manager did the job for me :)

Daniel

---

