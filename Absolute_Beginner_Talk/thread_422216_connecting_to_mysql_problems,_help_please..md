---
title: "connecting to mysql problems, help please."
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by ottawa on 2007-04-24
Hi,

server 6.10. I have installed mysql server & client 5. The server is running as I can see with ps -A mysqld  mysqld_safe

I am NOT able to conect for the first time and set the root password. 

xxxx@xxxx:/$ mysqladmin -u root password xxxxx
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

xxx = username / machine name

my.cnf is standard as I didn't change anything, except no bind to localhost.
What do I have to look for ?I am struggeling since 2 days with it and Linux is very new to me.

Thank you for any helpful suggestions

---

### Post by Drewski on 2007-04-25
I may be way out of my league here, but I'll give it a shot.

As I recall from my prior days of using MySQL on a Windows-based machine (and I don't think there is much difference) you are logging in incorrectly.

The proper login is as follows:

mysqladmin -u root -pxxxxx

There should be NO SPACE between -p and your password. Of course, this assumes you already have a root password set.

---

### Post by ottawa on 2007-04-25
Hi Drewski,

I am not even that far that I have the root password set. I am trying to do just that, and I am ending up with this error.

Don't know what to look for anymore. Any hint how to get the root password set ?

---

### Post by WilliamKB on 2007-04-25
I may be way out of my league - lol.

The first time I logged in to mysql on Ubuntu (way back when) I didn't use a password because 'root' doesn't have a default password.

Once I was in then I set the the 'root' password and created a new user with a password and never used 'root' again.

---

### Post by ottawa on 2007-04-25
WlliamKb

thanks for the hint. That makes sense as I read it. :) Should have figured that out myself. 
All over the place it's desrcibed as

mysqladmin -u root password your_password

to set the root password. And that gives me the Access denied error.
Will try that later today as I am at work right now. Hopefully it works.

---

### Post by bobbocanfly on 2007-04-25
In Fedora Core i got an Access denied error when trying to set the root password. I think i fixed it by going into the root account (Not su'ing), reinstalling MySQL then running it again. 

Saying that it did take a few tries.

---

### Post by slowhands36 on 2007-04-25
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
  

anyone familiar with this error when tryin to start mysql

I reinstalled and now it connected  but how do i get it to start mysql on bootup

---

### Post by ottawa on 2007-04-25
Hello all,

I still not able to get the root password set. I have installed now a third time. 
Mysql server IS running.
Here is part of my configuration file  /etc/mysql/my.cnf

[client]
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
language        = /usr/share/mysql/english
skip-external-locking
#
# For compatibility to other Debian packages that still use
# libmysqlclient10 and libmysqlclient12.
old_passwords   = 1
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
#bind-address           = 127.0.0.1
#

As I find all over instructions to set the passwort for user root, it's not working for me. I am out of ideas where to look.

maxima@yorkton:~$ mysqladmin -u root password 123456
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
maxima@yorkton:~$

Anyone try to give me a hint ? The suggestions mentioned didn't work. 

I don't want to give up !!

ottawa

---

### Post by ottawa on 2007-04-25
Hi,

my second try of posting:
I am not able to get the root password set after initial install of mysql database. I am trying since 2 days now and I have to admit the install on Windows was a piece of cake. This install is giving me real headaches.
My steps are running everytime no where. The server is up & running

one step out of a lot:

maxima@yorkton:/$ mysqladmin -u root password '123456'
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
maxima@yorkton:/$

The ONLY thing I changed in  /etc/mysql/my.cnf  was commenting out  bind = 127.0.0.1
Restarted the server and now what ???????  :confused: 

Someone here in this forum with mysql experience ?

---

### Post by WilliamKB on 2007-04-25
OK, try this exactly as you see it and type a new password when requested. Paste any negative results. Luck

mysqladmin -u root -p password

---

### Post by WilliamKB on 2007-04-25
OK, maybe I am out of my league.

I just uninstalled and reinstalled and I've got the same problem as you. I wish I had written down what I did before!!!!

---

### Post by ottawa on 2007-04-26
Hi WilliamKB

I found the solution. But I used the back-door as my front-door, will mean I did a google search with my error I got every time. Forget about the instructions I got and you mentioned, as you propably found the same as myself.

So here the way I was able to connect.

1. The only change I did to /etc/mysql/my.cnf   was to comment out bind-address = 127.0.0.1
2. at the command prompt

mysql -uroot -pyour-password mysql

Please not the important points: NO space between -u and root  like -uroot
The same with -p and your-password-of-choice

This IS the ONLY way I am able to set the password. I hope it works for you too. 
To check if mysqlserver is running and listening typ at the terminal prompt

 netstat -ta

and all server application should be listed.
I am crossing the fingers for you!!

ottawa

---

