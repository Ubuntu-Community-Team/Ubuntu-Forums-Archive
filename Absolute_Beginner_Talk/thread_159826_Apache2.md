---
title: "Apache2"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by mthakur2006 on 2006-04-13
How do u use LAMP?
I have no idea how to make it work.

---

### Post by kingmonkey on 2006-04-13
L= linux
A=apache
M=MySQL
P=PHP

what do you want to do with it?

---

### Post by mthakur2006 on 2006-04-13
Dear Kingmonkey,
I want to know what is it used for and how do you make it work.
Thanks,

---

### Post by indytim on 2006-04-13
Hi Mthakur2006,

Without getting boringly techno about it,  Apache is a web server. You need a web server to host web pages.  PHP is a parser.  The long and the short of a parser is that it converts programs (written in PHP) to web pages (that are hosted on the web server aka Apache).  MySQL is a relational database that holds data that php can access.  Thus the data in a MySQL database can be displayed using PHP in a web page within an Apache web server.

It's fun8) 

IndyTim

---

### Post by mthakur2006 on 2006-04-14
Dear Indytim,
Thanks for the information. But my problem is that I don't know how to make use of it - I mean how to host webpages on it. I mean how do u get your webpages on the localhost domain. :)
Thanks anyways.

---

### Post by indytim on 2006-04-14
Your local web pages will be content ( either .htm, .html or .php ) that are contained within your /www folder.  The url you would use for these pages is 
http://localhost/<mytest.htm>.

If php is configured properly (and it should be if you did the install recommended in the WIKI), you should be able to use the php extension and get htnl output.

for example
[PHP]<?PHP
print "This page is now working";
?>
[/PHP]

saves as test.php

the url would be [http://localhost/test.php](http://localhost/test.php)

There's literally tons of information and help out there on getting started in php and MySQL.  

One other thing that bears mentioning, is that this is a local web server.  You will need to do some adjustments if you want to share it beyond your local instance of Apache.  If this is the road you're heading down, again reference the WIKI and other reliable sources on security issues.

Good Luck,

IndyTim

---

### Post by mthakur2006 on 2006-04-14
Dear Indytim,
Thanks for the information. That is really appreciated.
Thanks,

---

