---
title: "Installing LAMP on Ubuntu 7.04 Desktop"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by esoterica on 2007-05-17
Searching the forums here pulled up so many posts that were not even close to what I'm wanting that I gave up on that. I also tried searching the documentation and I found bits and pieces of info, but actually need some slightly more specific information. If someone could just point me to the documentation for what I'm wanting that will hopefully be all the help I need on this. I thought I seen documentation on doing this the other day and thought I book marked it but now that I'm ready to do it I can't seem to locate it again.

I found this:
[https://help.ubuntu.com/community/ApacheMySQLPHP?](https://help.ubuntu.com/community/ApacheMySQLPHP?)

but it's not what I want, I need to run specific versions of Apache, PHP and MySql and the versions in the documentation I could find are not the ones I need and I believe require different library files and everything to work than the above docs specify.

These are the specific versions I was hoping to run, or at least as close to them as possible:
Apache version 1.3.37
PHP version 4.4.6
MySQL version 4.1.21-standard

It looks to me what I'm wanting to do is close to these instructions in the above documentation...

> 
To install the default LAMP stack in Ubuntu 6.06 LTS (Dapper Drake)

If you did not use the LAMP installer option from the server cd but want to install those same packages without having to reinstall your operating system, use any method to install the following packages

apache2 php5-mysql libapache2-mod-php5 mysql-server

All of those packages are in the Ubuntu 6.06 LTS (Dapper Drake) main repository. Once LAMP is installed, you need to set a mysql root password and then, depending on your web application, create a database, user and password. That's it! 


But I'm running on 7.04 Desktop not server and not 6.06 so I don't know if that makes a difference, also I'm not sure how to specify the correct versions I want, which like I said are not those versions mentioned in the docs?

---

### Post by Bachstelze on 2007-05-17
Given that PHP 4 is a security nightmare, it is not supported anymore so if you want it in Feisty, you'll need to compile it rom source.

---

### Post by esoterica on 2007-05-17
I was hoping to get as close to what I have on my live web server installed locally in Ubuntu, much of the stuff on my live web server is dependent on PHP4 is why, with mod_security installed I haven't had any security problems on it (yet).

I really would like to try out Apache2 and PHP5 on this local machine though, it's been something I've debated in my head all week trying to make up my mind. I don't want to have to compile from source, as this is primarily a desktop computer here at home and I like the automated updates, so based on what you just told me (thanks so much by the way) I suppose I should just go with the new stuff and consider updating my CentOS real world server.

So then will that documentation work for me to run Apache2 and PHP5 now with this sudden change of my plans? I ask because like I said I'm not using 6.06 or the server install.

Thanks again, not what I wanted to hear, but I think your pointing me in the better direction.

---

### Post by Bachstelze on 2007-05-17
There's not really much point in running Apache 2. I'm personnally running Apache 1.3 and PHP5 on my home webserver with no problem :)

EDIT : but it seems the Apache 1 modue for PHP5 is not in the Feisty repos either, you'll have to go with Apache 2. Or build from source ;)

---

### Post by esoterica on 2007-05-17
I'm fine with that as well then, is there something as easy as "apt-get lamp" I can run in Ubuntu to just knock it all out quickly like that or am I being too lazy with that dream? 

Those docs seem to lean towards Apache2 I couldn't see a clear way to grab or speciy 1.3 for Apache

---

### Post by esoterica on 2007-05-17
Just seen your edit, since I'm not easily going to have what I want (probably why I couldn't find the info) will those instructions for 6.06 work for me then or do I need to do anything different to accommodate 7.04 desktop?

---

### Post by Bachstelze on 2007-05-17
Yes, those instructions should work in Feisty too :)

---

### Post by esoterica on 2007-05-17
Alright then, thanks so much, that's what I'm heading off to play with right now, the docs make it look straightforward enough to get it installed, I seen some other docs already on the detailed configuration once installed so I guess I'm off to get busy doing it.

Thanks again Hymn ToLife, your posts are always very helpful around here, your a real asset to me and the community!

---

