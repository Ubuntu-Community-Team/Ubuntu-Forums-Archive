---
title: "installing LAMP. I got LA but how I get MySql?"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-03-15
So I found a cool site for those that are using Dapper.

I already have L which is ubuntu, I just installed Apache server.
sudo apt-get install apache2
Then I tested with this: * [http://localhost](http://localhost) yay! It works is what it says. Can someone tell me how I make a simple Hello world test on this guy?

So now I am stuck with installing mysql server
[http://ubuntuguide.org/wiki/Dapper#How_to_install_MYSQL_Database_Server](http://ubuntuguide.org/wiki/Dapper#How_to_install_MYSQL_Database_Server)
so i did this:
1. sudo apt-get install mysql-server
2. gksudo gedit /etc/mysql/my.cnf
3.  * Find the line bind-address = 127.0.0.1 and comment it out 
#bind-address           = 127.0.0.1

<This is the part I am stuck with> 
So the website says this...
    * MySQL comes with no root password as default. This is a huge security risk. You'll need to set one. So that the local computer gets root access as well, you'll need to set a password for that too. The local-machine-name is the name of the computer you're working on. For more information see here 

mysqladmin -u root password your-new-password
mysqladmin -h local-machine-name -u root -p password your-new-password
sudo /etc/init.d/mysql restart


so on my prompt i typed:
apple@apple-desktop:~$mysqladmin -u root password master

i got this:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
[COLOR="Red"]Why?? can someone tell me what i did wrong?[/COLOR]

the other thing is, what is my 'local-machine-name', is it apple-desktop?

---

### Post by trippinnik on 2007-03-15
I'm stuck here to.  My machine name is tripp but now I get this error: 
nik@tripp:~$ mysqladmin -u root password XXXXXXXXXXX
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

---

### Post by scxtt on 2007-03-15
you shouldn't need to specify a "local-machine-name" since you're connected to the machine you're trying to connect to (localhost) ...

and i think you should use: mysql -u root -p "your password"
(for more "security", don't use "your password" from the command line - just use **mysql -u root -p** and you'll be prompted for the p/w [so it won't end up in your ~/.bash_history]) ...

---

### Post by garybrlow on 2007-03-15
The easiest and fastest way to install and use LAMP and then some is to use a third party app called XAMPP its available for Linix, Windows, OSX, and Solaris found here [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html). It installs everything you need and more. Check it out.

Cheers!!!

GaryBrlow :biggrin:

---

### Post by indytim on 2007-03-15
Or you could use the Ubuntu WIKI at:

[LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP")

I've used it on 3 installs already.

IndyTim

---

