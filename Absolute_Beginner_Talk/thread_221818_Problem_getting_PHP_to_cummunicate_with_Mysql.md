---
title: "Problem getting PHP to cummunicate with Mysql"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by lekoya on 2006-07-24
Hi there, I cant get php to cummunicate with mysql. I have started mysql service and evertything is fine. When connect to database then i get this error: "**Call to undefined function mysql_pconnect()**".

I have tried everything, but maybe i am  missing something somewhere. 
Please Help.

Thank you.

---

### Post by risbac on 2006-07-24
By default in recent PHP packages, you don't have all the modules. You might want to install php5-mysql if you are using Php5 of course. This will download and install the mysql module for php, and you should be fine.

---

### Post by lekoya on 2006-07-24
Thanks for quick response. but i have  already tried this command:
'sudo apt-get install php5-mysql --fix-missing' and it displays the following output : "Reading package lists... Done
Building dependency tree... Done
php5-mysql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
"

Is there anything else i can try??

---

### Post by risbac on 2006-07-24
Check in the configuration file of php if the mysql extension is loaded.
It should be somewhere in /etc/php..../...../....
Can't remember the exact place, but it's there, only one file. There are two things to check:

first, module loaded, do you see mysql.so somewhere there? I think it's the name of the file. 

second, extension folder. It should be something like /usr/lib/php5/ext/
Once you have this info, check if you have the extension file (mysql.so) in this directory. It could be somewhere where. Locate it, copy it in this /ext/ folder. Restart your Apache, and try again.

---

### Post by lekoya on 2006-07-24
Thanx risbac,
But i have checked php.ini file, but it has msql.so module and NOT mysql.so.

And this path does not exist :  /usr/lib/php5/ext/

i cud only get up to here:  /usr/lib/php5/ 
This are the only folders under this path: /20051025  /libexec  /maxlifetime

Maybe i am missing somwthing somewhere, but i dont know what

Pls help

---

### Post by risbac on 2006-07-24
OK, try this: 

```
locate mysql.so
```

I think you will find it in /usr/lib/php5/20051025/

Now:

> sudo mkdir /usr/lib/php5/ext
sudo cp /usr/lib/php5/20051025/mysql.so /usr/lib/php5/ext/


We create the "ext" dir, and copy the extension file in it.

Now let's enable this extension in php:

> sudo gedit /etc/php5/apache2/php.ini

look for "extension_dir" in the php.ini file. 

If should be equal to "/usr/lib/php5/ext/".

If it's not, set it plz, between double quotes.

Now lower in "Dynamic Extensions", just add this line:

```
extension=mysql.so
```


Save, exit, restart the indian, and tell me.

---

### Post by lekoya on 2006-07-24
> **risbac said:**
> OK, try this: 

```
locate mysql.so
```

I think you will find it in /usr/lib/php5/20051025/

Now:



We create the "ext" dir, and copy the extension file in it.

Now let's enable this extension in php:



look for "extension_dir" in the php.ini file. 

If should be equal to "/usr/lib/php5/ext/".

If it's not, set it plz, between double quotes.

Now lower in "Dynamic Extensions", just add this line:

```
extension=mysql.so
```


Save, exit, restart the indian, and tell me.
Thanx risbac,

I did exactly as what you said abouve and **Everything is working fine now**. I would invite you for some drinks if you were in South Africa.

I really appreciate your help. You are the man.

And thanks to everyone who participated in this Topic. Much Appreciated.

Thanx a million.

Lekoya

---

### Post by risbac on 2006-07-24
Great, good to see it's working. 
Normally it's not that complicated. If you install php5-mysql after php5, it should update php.ini. And I'm not sure it's placing the extension in the right directory though, I don't understand why. 

Anyway, now you know more about php, next time you will be the one helping someone on the forums :)

---

### Post by jelly on 2006-08-03
risbac: Thanks so much for this information, I had exactly the same problem and I'm sure I would have wasted days trying to figure it out - but after following those few simple steps you laid out everything is working perfectly.

This information should clearly go in the wiki somewhere.

Thanks again,

- Jelly.

---

### Post by risbac on 2006-08-03
You are totally right Jelly, it's better to put this solution in the wiki somewhere. I updated the [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) page, now there are info about the mysql/php activation problem. I hope it will help some persons until they place the files in the right directory from the installation.

---

### Post by suoko on 2006-12-22
One question: how can phpmyadmin use php+mysql anyway (I mean without the reported modification)?

---

