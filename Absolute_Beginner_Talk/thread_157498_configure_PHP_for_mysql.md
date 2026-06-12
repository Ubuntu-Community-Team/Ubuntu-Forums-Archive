---
title: "configure PHP for mysql"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by entropy7 on 2006-04-09
Hi-
this is my first post... hope this works.

a friend of mine got apache, PHP5, and MySQL running on my Ubuntu 5.1 system.
I created a database that i can access from the command line using the
MySQL monitor and i can execute PHP script. 

but when i call the function, mysql_connect, it says it is undefined. I have instructions 
for interfacing PHP and MySQL, but they say, "Go into the Windows directory and change the php.ini file, blah, blah, blah" 

So how do i configure PHP5 on an Ubuntu system?
Thanx

---

### Post by adamkane on 2006-04-09
First decide if you need PHP5. It is MUCH easier to install/maintain PHP4 on Breezy.

If you must have PHP5:
[http://doc.gwos.org/index.php/Latest_Apache_and_PHP](http://doc.gwos.org/index.php/Latest_Apache_and_PHP)

If you can live with PHP4:
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by sands on 2006-04-09
Have u installed php5-mysql module??
If not install it thru synaptic package manager...

---

### Post by entropy7 on 2006-04-09
I went into the Synaptic Package Manager.  There are various packages for MySQL and PHP. all of which appear to be installed.  On my system, i did not have any package called php-mysql.

---

### Post by sands on 2006-04-09
Its php5-mysql..Hope u searched for it..
add all the repositories available in synaptic.everthing
U can do this in synaptic thru settings->repos
after that click reload..
then u can see php5-mysql.

---

### Post by entropy7 on 2006-04-09
i can go into settings->repositiories but I see this scroll list of about 10 items referring to ubuntu ver. 5.10, "Breezy Badger", "updates", "security updates". u said, "after that click reload"... i don't see any "reload" buttons.

---

### Post by entropy7 on 2006-04-09
Oh wait, u mean the reload button at the very front. That did it! PHP now recognizes the mysql_connect function. Thanx.

---

### Post by arcadefx on 2006-04-12
Also, after I upgraded to PHP5 I had to restart apache2 as super-user (sudo):

% /etc/init.d/apache2 restart

My content management system written in PHP4 ended up w/ zero issues, which is great!  I didn't have to change any code.

:)

---

### Post by sands on 2006-04-13
Yeah! its Compatible..

---

### Post by MenZa on 2006-04-13
Honestly -- wouldn't it be easier just to install [XAMPP](http://www.apachefriends.org/en/xampp.html)?

---

### Post by sands on 2006-04-13
I donno abt XAMPP..
But its easy to install apache,php and mysql using synaptic..
Of course everything is easy to install thru synaptic..

It seems tat XAMPP has a lot of things preinstalled..Interesting..
There is a step by step installation guide at their site [http://www.apachefriends.org/en/xampp-linux.html#372](http://www.apachefriends.org/en/xampp-linux.html#372)
(you might know)

---

### Post by adamkane on 2006-04-21
XAMPP installs a lot of packages, and it is difficult to troubleshoot any problems, when you have a dozen packages all tied together. Works for some people, but probably not good for beginners.

For simplicity, stick to Apache2 PHP4 and MySQL4. After you get used to configuring apache/php/mysql, start installing other packages.

You will get lost, if you try to install all the latest stuff all at once. Very few people will be able to help you troubleshoot, if you try to install the latest and greatest without building a foundation of knowledge/experience first.

---

