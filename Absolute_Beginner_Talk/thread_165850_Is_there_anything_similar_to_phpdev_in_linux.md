---
title: "Is there anything similar to phpdev in linux?"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-25
I use PHPDEV on Windows ... it was a really good way to install three packages in one  package. is there anything similar to this in Linux?

---

### Post by Ensnared on 2006-04-25
Sort of...
```
sudo apt-get install apache2 php5 mysql-server
```...or if you want PHP4 instead of PHP5:
```
sudo apt-get install apache2 php4 mysql-server
```
This will install them all on your system and set it up. I'm not familiar with PHPDEV, but a quick search seems to indicate that this is exactly what it does (much like xampp, except that does a lot more).

You may also want to install phpmyadmin to manage your MySQL databases, in which case you simply do this:```
sudo apt-get install phpmyadmin
```

You may also need to set a password for the "root" user in MySQL after it's installed. You do this with the following command:```
mysqladmin -u root password "thepasswordyouwant"
```...and you'll be able to log in with username "root" and password "thepasswordyouwant" in phpmyadmin (or any other frontend for the MySQL database-server).

---

### Post by Isoss on 2006-04-25
I did exactly what you suggested and here is what it told me
```
Reading package lists... Done
Building dependency tree... Done
Note, selecting apache2-mpm-worker instead of apache2
apache2-mpm-worker is already the newest version.
E: Couldn't find package php5

```

I have apache installed. will that affect the process in any how incase php worked?

---

### Post by Ensnared on 2006-04-25
[QUOTE=Isoss]E: Couldn't find package php5
[/QUOTE]"There's your problem" ;)

Maybe you have to enable the universe/multiverse repositories in your /etc/apt/sources.list first (then run "sudo apt-get update"). I'm not sure which repository PHP is located in. Optionally, try just "php" or "php4" instead, but chances are you'll still need to enable the repositories.

---

### Post by Isoss on 2006-04-25
alright, that's what I did before you tell me and go here and check what happened:
[http://www.ubuntuforums.org/showthread.php?p=956560&posted=1#post956560]("http://www.ubuntuforums.org/showthread.php?p=956560&posted=1#post956560")
I dunno why it's doing that ... you can post your help there.

---

### Post by adamkane on 2006-04-26
Standard installs:

Breezy:
 
 ```

 sudo apt-get install apache2 php4 mysql-client mysql-server libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql phpmyadmin
 
``` 
 Dapper:
  
  ```

 sudo apt-get install apache2 php5 mysql-client mysql-server libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql phpmyadmin
 
```

---

