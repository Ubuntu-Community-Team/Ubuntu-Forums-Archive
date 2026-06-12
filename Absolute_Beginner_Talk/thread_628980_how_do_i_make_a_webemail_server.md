---
title: "how do i make a web/email server"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by jay43228 on 2007-12-01
:KS i am wanting to build a website/email server and i brand new to all this.. is there a super easy guide to going this? i want a list a 6 pages on my website and host 3 email account with web log in:KS

specs
hp a305w
2.7ghz Intel core 478 
512 ddr ram
250 gd hard drive
cd rom

also i have "Dynamic IP" isp does offer any thing else so i need a work around:confused:


any help would be great 
thanks

---

### Post by bwald on 2007-12-02
As far as setting up your website, that is very easily done by installing an apache server and hosting all of your files locally.  First install apache

```
sudo apt-get install apache2
```

Then you'll want to configure apache, the main configuration file is located at /etc/apache2/httpd.conf.  In this file you will set a "DocumentRoot" directive, which is where you'll keep all of the files you'll be serving.  This is usually set to /var/www as default.  

If you want to use a dynamic IP to host the site, you'll need to set up a "dynamic hostname."  This is a static name which will always redirect to your current IP.  There are several sites which provide them, I personally use dyndns.org.  You'll need to sign up for a dynamic hostname, and also download a program to tell dyndns.org (or whoever you choose to provide your hostname) when your IP changes.  The program [_ddclient_]("http://ddclient.wiki.sourceforge.net/") a perl-based program to automatically update your dynamic hostname whenever you IP changes.  


For setting up a mail server, [_this HowTo_]("http://ubuntuforums.org/showthread.php?t=40047&highlight=howto+mail+server") is incredibly detailed and probably far more than you need.

---

