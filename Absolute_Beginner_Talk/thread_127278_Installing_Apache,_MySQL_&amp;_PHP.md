---
title: "Installing Apache, MySQL &amp; PHP"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by Nyati on 2006-02-08
Evening people

I'm having a problem installing php on my system. I've installed Apache, MySQL and attempted installing PHP-5.1.2 but when I extracted it, it had a problem I think as it had a "no-entry" icon over the top of it. After re-attempting this many times I downloaded and successfully extracted PHP-4.4.2.

However, after typing in the following while logged in as root:

[COLOR="SeaGreen"]#./configure -prefix=/usr/local/php -with-apxs2=/usr/local/apache2/bin/apxs -with-mysql=/usr/local/mysql[/COLOR]

I got this response,

[COLOR="SeaGreen"]loading cache ./config.cache
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether gcc and cc understand -c and -o together... yes
checking how to run the C preprocessor... gcc -E
checking for AIX... no
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking for re2c... exit 0;
checking whether ln -s works... yes
checking for gawk... no
checking for mawk... mawk
checking for bison... no
checking for byacc... no
configure: warning: You will need bison if you want to regenerate the PHP parsers.
checking for flex... lex
checking for yywrap in -ll... no
checking lex output file root... ./configure: line 2540: lex: command not found
configure: error: cannot find output from lex; giving up[/COLOR]

Not sure what most of this meant, I tried to "make" and got the following response,

[COLOR="SeaGreen"]# make make: *** No targets specified and no makefile found.  Stop.[/COLOR]

Can someone please help me?

---

### Post by TrendyDark on 2006-02-08
I believe you need to install build-essential, just apt-get it. If you're looking to install Apache2 and PHP5, you can do so via apt-get. I have done it in the past and it's a lot easier than compiling them both.

build-essential:

```
sudo apt-get install build-essential
```

---

### Post by David Corrales on 2006-02-08
I agree with the suggestion about using the packaged versions. It'll make your life a lot easier.
The thing with ubuntu is that they omit the regular build tools so you'll have to run *configure* a lot of times, each time adding whatever else is that you need.
For example, *lex* is a tool used to handle gramatic patterns for text recognition and stuff. It's used to build compiler chains.

---

### Post by kaamos on 2006-02-08
Easy way out: [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by Nyati on 2006-02-08
Thanks, I'll try everything but before I use the packages do I need to delete the Apache, MySQL and PHP packages I've already installed?

---

### Post by TrendyDark on 2006-02-08
You shouldn't, it'll most likely remove them for you. But just to be safe, you might want to.

---

### Post by kaamos on 2006-02-08
Just in case, that is probably a good idea.

---

### Post by Nyati on 2006-02-08
Hi

I think I've updated the correct repositories but still get the following response when I 

# sudo apt-get install php5
Reading package lists... Done
Building dependency tree... Done
php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


What do I do now?

---

### Post by Nyati on 2006-02-09
I've installed apache and mysql but am having problems installing php. I've taken the advice of downloading the php package from the repository but not sure if I downloaded the correct one.

Can someone tell me which is the correct one and how can I get this php to work with apache and mysql?

Many thanks in advance.

BTW I only realised that apache and mysql were working, when I logged off and noticed them shutting down.

---

### Post by Snower on 2006-05-23
apt-get install flex to solve the lex problem

---

### Post by hotbrainz on 2006-05-24
I have lamp running in my system i.e PHP , MySQL and Apache. The easiest w2ay by far i found was this..

[Xampp]("http://www.apachefriends.org/en/xampp-linux.html")

This is extremely easy to install and just follow the instructions.

---

### Post by adamkane on 2006-05-24
Xampp installs a bunch of apps that are a PITA to troubleshoot. 

Install LAMP this way:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

---

