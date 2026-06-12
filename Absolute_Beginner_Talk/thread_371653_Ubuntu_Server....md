---
title: "Ubuntu Server..."
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by DukeZenAku on 2007-02-27
Hi all, i'm new in this Linux world and this "site-development" world to, so i like to ask.

Ubuntu Server is the best OS to a Web Server? i'm trying to find a cool OS, not to much complicated and stable, but anyone in this world talk about the Ubunt "instanble" nature, it's true? what kind of problem's i can have with Ubunt in a server?

(if someone know what freewares i can use to: forum's, e-mail and more please tell me)

Sorry start annoyng but it's a "old' doubt, thank's if you can help me, and sorry by my bad english, byes Ds...

---

### Post by SeanTater on 2007-02-27
Ubuntu is not entirely geared toward the server, that's true. But that's not to say it isn't stable. You can just as easily create a server in Ubuntu as Debian or Red Hat. (I've even created one on Linspire.)

Most servers can be installed like so:

Web (HTTP) server: one of the following:
```
 sudo apt-get install apache2 
```
OR
```
 sudo apt-get install lighttpd 
```

Mail:
SMTP:
```
 sudo apt-get install exim4 
```
OR
```
 sudo apt-get install postfix 
```
OR
```
 sudo apt-get install courier-mta 
```
POP:
```
 sudo apt-get install courier-pop 
```
IMAP:
```
 sudo apt-get install courier-imap 
```

FTP:
```
 sudo apt-get install proftpd 
```

SSH:
```
 sudo apt-get install openssh-server 
```

Database
```
 sudo apt-get install mysql-server 
```
OR
```
 sudo apt-get install postgresql 
```

However, each of these servers **really should** be configured.
Chances are, you want a web server. install one and put your HTML files in /var/www and your CGI files in /usr/lib/cgi-bin. You will have to be root, to put anything in those directories, but you can change the owner to you so you don't have to constantly sudo..

---

### Post by bodhi.zazen on 2007-02-27
Here are some server guides (for Ubuntu) :

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

[http://doc.gwos.org/index.php/ServerGuide](http://doc.gwos.org/index.php/ServerGuide)

[http://www.ubuntuforums.org/showthread.php?&t=223805](http://www.ubuntuforums.org/showthread.php?&t=223805)

In the end, I think it is a matter of preference ...

I might look at Centos ...

---

### Post by az on 2007-02-27
> **DukeZenAku said:**
> what kind of problem's i can have with Ubunt in a server?.

See here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The LAMP stack is rock-solid in Ubuntu.  Now, depending on what you run on top of that may complicate your life.  

> **DukeZenAku said:**
> 

(if someone know what freewares i can use to: forum's, e-mail and more please tell me)


There is no freeware here.  The software that powers Ubuntu is free-libre software.  There is a huge difference.

To install web applications, see the section in this page:
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
[https://help.ubuntu.com/community/Servers#head-ed0a847767fb61cd99eed5e6b641c2ccf11cdea4](https://help.ubuntu.com/community/Servers#head-ed0a847767fb61cd99eed5e6b641c2ccf11cdea4)



> **SeanTater said:**
> Ubuntu is not entirely geared toward the server, that's true. 

No, that's false.  Ubuntu is even an officially supported OS for some of the higher-end Sun servers - Ubuntu even outperforms Solaris on them.


> **SeanTater said:**
> 
Most servers can be installed like so:

Web (HTTP) server: one of the following:
```
 sudo apt-get install apache2 
```
OR
```
 sudo apt-get install lighttpd 
```
Database
```
 sudo apt-get install mysql-server 
```
OR
```
 sudo apt-get install postgresql 
```
...
You will have to be root, to put anything in those directories, but you can change the owner to you so you don't have to constantly sudo..


See the apachePhpMysql page instead.  You will have an easier and time and it may be safer as well.

---

