---
title: "Apache2 manually installed, php5 problems"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by nitro_n2o on 2007-05-31
Hi all, 
So i have been trying to solve this problem for the last week, so it's great if someone can help me out. 
I have installed apach2 from apt-get but never work for really weired mistakes!! 'Order' and 'Deny' and stuff like that in the default apache2.conf are giving me errors.. 
Anyways, i downloaded apache2 and compiled it myself (yes fun) but now i get php5 to work :( i have everything related to php5 but how do i connect it to my apache installation.. 
my apache2 dir is in /usr/local/apach2/ and php5 is in /etc/php5

Thx...

---

### Post by empthollow on 2007-05-31
hmm, i installed both apache2 & php from repositories and i don't recall having to do anything special to connect the 2.  what are you using to test if php is working?

---

### Post by Cypher on 2007-05-31
If you want to go the PHP as a CGI way, you'll have to add some AddHandler options to your apache2.conf file to direct .PHP files to the executable. But that's a lot of work..

Follow my post [here]("http://ubuntuforums.org/showpost.php?p=2638509&postcount=5") which details the steps I took to get Apache/MySQL/PHP up and running. 

Ping back if those setps don't work and what exact issues where you having with "Order" and "Deny"??

---

### Post by nitro_n2o on 2007-05-31
I just use a  .php file and try to open in firefox, which prompts me to download it instead of parsing it?

---

### Post by Cypher on 2007-05-31
> **nitro_n2o said:**
> I just use a  .php file and try to open in firefox, which prompts me to download it instead of parsing it?
And that's the expected response if you don't have the ph5-mod for Apache or you don't add the appropriate AddHandler to apache2.conf

---

### Post by nitro_n2o on 2007-05-31
I'm trying to use apache from apt i get this 
```

Invalid command 'Allow', perhaps misspelled or defined by a module not included in the server configuration
```
and the same for Deny, Order, .... 
what should i edit to let apache2 know where php5 is?

---

### Post by Cypher on 2007-05-31
A couple of links for you to look at:
[http://www.onlamp.com/pub/a/php/2001/03/29/php_admin.html](http://www.onlamp.com/pub/a/php/2001/03/29/php_admin.html)
[http://www.thesitewizard.com/archive/php4install.shtml](http://www.thesitewizard.com/archive/php4install.shtml)

---

### Post by nitro_n2o on 2007-05-31
so i added: 

AddHandler php-script .php 

The same problem :(

---

### Post by annda on 2007-05-31
do you have libapache2-mod-php5 module installed, as Cypher suggested?

can you see php in 

/etc/apache2/mods-enabled

---

### Post by nitro_n2o on 2007-05-31
> **annda said:**
> do you have libapache2-mod-php5 module installed, as Cypher suggested?

can you see php in 

/etc/apache2/mods-enabled

well, i have libapache2-mod-php5 but the problem is i don't have /etc/apache2/mods-enabled/ 
i compiled the whole thing from source and it's all in /usr/local/apache2 and there is no mods-enabled directory their neither...

---

### Post by annda on 2007-05-31
i'm pretty sure you have apache files elsewhere even if you compiled from source... can you search for mods-enabled or even apache2 to find out where the modules are stored? in my case php5.load and php.conf are important.

use sudo updatedb and locate if you have problem searching.

---

### Post by annda on 2007-05-31
this is rather old fashioned, but you can always try to add the line to apache2.conf or httpd.conf

AddType application/x-httpd-php .php

and restart apache.

---

### Post by nitro_n2o on 2007-05-31
i have AddType application/x-httpd-php php since the start, but doesn't work.. 
I have two copies of apache2 one is installed using apt-get and it's in /etc/apache2 
and the other (which i use) that i compiled in /usr/local/apache2 and I'm sure that there is no mods-enabled in that directory? I really don't feel like installing a new ubuntu now.. any ideas will be appreciated... thx

---

