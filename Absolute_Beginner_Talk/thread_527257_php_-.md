---
title: "php -"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by jakebur01 on 2007-08-16
i installed ubuntu 7.04 server edition.... installed gui.... and then installed Webmin 1.360..

I am able to see a test html page under my root folder when I type my domain into the url.
var/www/   = is the root directory where i put the test.html page

My problem is that when I put a php page into that directory... it ask me to download that page rather than it parsing the php.

___________________________

in webmin i went to > PHP Configuration> and put this
/etc/php5/cli/php.ini    | configuration for mod_php
/etc/php5/cli/php.ini    | configuration for scripts run via CGI
/etc/php5/cli/php.ini   | configuration for command-line scripts

_________________ I dont know if that was right_________

Is their somewhere in the php.ini where i need to put var/www/ as the root directory?

How do I know whether php is even running?

Thanks,

Jake

---

### Post by heimo on 2007-08-16
Did you install libapache2-mod-php5 or libapache2-mod-php4?

---

### Post by jakebur01 on 2007-08-16
I don't recall. How do I check?

---

### Post by heimo on 2007-08-16
> **jakebur01 said:**
> I don't recall. How do I check?
If you use Synaptic Package Manager to install stuff, search for the package and see if it's installed. Or run something like:

```
apt-cache search libapache2-mod-php5
```And see if the first character at the beginning of the line is i like installed.

Or run:
```
dpkg --get-selections | grep libapache
```and see if that packages status is "install"

EDIT: apt-get -> apt-cache

---

### Post by jakebur01 on 2007-08-16
it says:
```
E: Invalid operation search
```

---

### Post by heimo on 2007-08-16
> **jakebur01 said:**
> it says:
```
E: Invalid operation search
```

 My mistake. It's apt-cache, not apt-get.

---

### Post by jakebur01 on 2007-08-16
when i try:
```
dpkg --get-selections | grep libapache
```
it doesn't do anything.

---

### Post by jakebur01 on 2007-08-16
Ok.
apt-cache search libapache2-mod-php5

returned:

libapache2-mod-php5 - server-side, html-embedded scripting language (apache 2 module)
php5-cgi - server-side, html-embedded scripting language(CGI binary)

---

### Post by heimo on 2007-08-16
> **jakebur01 said:**
> when i try:
```
dpkg --get-selections | grep libapache
```it doesn't do anything.

You don't have Apache PHP module installed. That's your problem.

---

### Post by jakebur01 on 2007-08-16
What do I need to do?
Sir.

---

### Post by heimo on 2007-08-16
> **jakebur01 said:**
> What do I need to do?

Install Apache PHP module. It's in a package libapache2-mod-php5 or libapache2-mod-php4, depending on the version of PHP.

Instructions how to install software:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

There are tutorials on these forums how to install Apache with PHP support.

---

### Post by jakebur01 on 2007-08-16
Is this not something I could install or run off my server 7.04 i386 cd?

---

### Post by heimo on 2007-08-16
> **jakebur01 said:**
> Is this not something I could install or run off my server 7.04 i386 cd?
I don't know if that CD has Apache PHP module. If you have network connection, you should be able to install it using apt-get.
```
sudo apt-get install libapache2-mod-php5
```or
```
sudo apt-get install libapache2-mod-php4
```

---

### Post by jakebur01 on 2007-08-16
oh man.... thank you so much

---

