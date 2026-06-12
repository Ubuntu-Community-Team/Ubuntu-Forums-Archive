---
title: "phpinfo page"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by zebog13 on 2008-03-12
Configuration File (php.ini) Path 	/etc/php5/apache2
Loaded Configuration File 	(none)
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
additional .ini files parsed 	/etc/php5/apache2/conf.d/php.ini

Questions given above information:
1)If the php.ini is located, why is it not loaded
2)Is there a way for a directory NOT be scanned?

---

### Post by neurostu on 2008-03-12
Can you rephrase your questions?

---

### Post by zebog13 on 2008-03-12
> **zebog13 said:**
> Configuration File (php.ini) Path 	/etc/php5/apache2
Loaded Configuration File 	(none)
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
additional .ini files parsed 	/etc/php5/apache2/conf.d/php.ini

Questions given above information:
1)If the php.ini is located, why is it not loaded
2)Is there a way for a directory NOT be scanned?

The top 4 lines are part of my php_info().
1) As you can see, php recognizes a configuration file in line 1, but line two states it is not loaded. Why is this?
2)How do I make lines 3 & 4 not happen, I only have/need 1 .ini file

---

### Post by raptor2552 on 2008-03-12
I would first check to see that you have a php.ini file in /etc/php5/apache2 and that it is readable, my guess is it missing or not readable.

As for the other .ini files,  /etc/php5/apache2/conf.d is a symbolic link to  /etc/php5/conf.d where you'll find other configuration files like gd.ini, mhash.ini, mysql.ini among others, of course dependant on what mods you want loaded.

If it were me, I'd try to find out why the  /etc/php5/apache2/php.ini file isn't loading.

---

### Post by neurostu on 2008-03-12
I agree, check the permissions of your file.  Make sure it is universably readable

---

### Post by zebog13 on 2008-03-13
> **raptor2552 said:**
> I would first check to see that you have a php.ini file in /etc/php5/apache2 and that it is readable, my guess is it missing or not readable.

As for the other .ini files,  /etc/php5/apache2/conf.d is a symbolic link to  /etc/php5/conf.d where you'll find other configuration files like gd.ini, mhash.ini, mysql.ini among others, of course dependent on what mods you want loaded.

If it were me, I'd try to find out why the  /etc/php5/apache2/php.ini file isn't loading.

my conf.d folder is empty minus the php.ini. But I think what you're trying to say, is that there is no way to stop scanning for other .ini files. Correct me if I'm wrong
As for my php.ini, I changed permissions to 755, and even the group to www-data. Restarted apache2, and still no go.

---

### Post by OffAxis on 2008-03-13
My permissions on the php.ini are set to

```
-rw-r--r-- 1 root root 44298 2008-01-28 07:11 php.ini

```

---

### Post by OffAxis on 2008-03-13
> my conf.d folder is empty minus the php.ini.
The php.ini file shouldn't reside in the conf.d folder; it should be in 
```
/etc/php5/apache2/php.ini
```

> )If the php.ini is located, why is it not loaded
It may be set up to initialize with the php.ini file from the /etc/php5/apache2/ folder, and just look to the conf.d folder for module configuration.
Try moving the php.ini file to the appropriate folder and restart your server.

---

### Post by zebog13 on 2008-03-13
> **OffAxis said:**
> The php.ini file shouldn't reside in the conf.d folder; it should be in 
```
/etc/php5/apache2/php.ini
```


It may be set up to initialize with the php.ini file from the /etc/php5/apache2/ folder, and just look to the conf.d folder for module configuration.
Try moving the php.ini file to the appropriate folder and restart your server.

Very well done!!! 
To stop scanning, I just removed folder that it requires to scan.

---

