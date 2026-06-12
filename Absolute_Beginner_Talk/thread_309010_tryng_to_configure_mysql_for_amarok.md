---
title: "tryng to configure mysql for amarok"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by tee2 on 2006-11-29
I'm trying to configure mysql for amarok. How do I start the daemon and where is it located? I think I have mysql installed but its not in the applications  menu. Actually a lot the applications I've installed aren't, how do I get them to show up?

edit: Where do installed applications install to? :/

---

### Post by benuski on 2006-11-29
Installed applications go lots of different places.  The first thing you should try is to just type the name of the package into the command line; a lot of times that gets the program working.  If that doesn't work, go into Synaptic and find the package you installed, go to properties, and then to installed files.  Look for the files that are installed either in /bin or in /sbin.  Those will be the executable files, so just type the name of that into the command line and it should work.

---

### Post by tee2 on 2006-11-29
I just tried this:

```
tee@tee-laptop:~$ mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
tee@tee-laptop:~$ 


```

---

### Post by benuski on 2006-11-29
Did you try the second strategy?  I'm fairly sure that there is no mySQL server install by default, you have to go to Synaptic and install it.  The current one in the repos is 'mysql-server-5.0'.

---

### Post by tee2 on 2006-11-29
> **benuski said:**
> Did you try the second strategy?  I'm fairly sure that there is no mySQL server install by default, you have to go to Synaptic and install it.  The current one in the repos is 'mysql-server-5.0'.
I installed mysql-server-5.0. I can't figure out how to run the daemon and configure it though.

---

### Post by koshari on 2006-11-29
install myphpadmin, then simply browse with firefox to localhost and set up mysql there.

---

### Post by tee2 on 2006-11-29
Okay I installed phpmyadmin, how do i set it up? I tried browsing to both localhost and 127.0.0.1 but neither worked.

Sorry, I'm really a noob at linux.

---

### Post by angkor on 2006-11-29
[http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo#MySQL_Setup](http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo#MySQL_Setup)
[http://www.ubuntuforums.org/showthread.php?t=187236&highlight=mysql+amarok](http://www.ubuntuforums.org/showthread.php?t=187236&highlight=mysql+amarok)

Maybe this helps.

---

### Post by adamkane on 2006-12-05
Install apache, php, mysql and phpmyadmin. You will need to pick one of the following options.

Apache2 + PHP4 + MySQL4:
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2 + PHP5 + MySQL4:
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2 + PHP5 + MySQL5:
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot or start Apache/MySQL this way:
```

sudo /etc/init.d/apache2 start
sudo /etc/init.d/mysql start

```

Open phpmyadmin in your browser:
[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

Log into phpmyadmin:
Name: root
Password: [blank]

In phpmyadmin, create a database called amarok.

In phpmyadmin, add a user with or without a password.

Open amarok, and enter the database name, user name, and user password.

---

### Post by lopzided on 2006-12-13
adamkane, thanks for that mini-howto....i just reinstalled, and the site (amarok.kde.org, i think it was) that hosted the howto i followed last time was down!

---

### Post by Tjoels on 2007-01-06
Hey, i followed this guide, and amarok was able to connect to the database, (at least it didn't complain....) but when i say rescan collection, nothing happends. :-? 

Any special setting or preparation like making a table on the database, i need to change?

In phpMyAdmin, in Database: amarok -> Operations -> Collation:, what should the charset be set to there? The default 'Collation' was 'latin1_swedish_ci', even though i'm not from sweden.

---

### Post by osarusan on 2007-02-01
I've followed the instructions, and Amarok connects to my database just fine... but while it's rescanning my collection it reaches 71% and then hangs indefinitely... my whole system grinds to a halt, even if I close Amarok, and I needeed to reboot. Does anyone have any idea what's going on, or how I can fix it?

Thanks

---

### Post by KeithWatson on 2007-02-18
Thanks for the instructions.  I made the rookie mistake of installing the MySQL client rather than the MySQL server.  I kept getting error code 2000 when I tried to set the password for MySQL and had the hardest time figuring out what I had done wrong.  I just thought I might post my experience in case anyone else makes the same stupid mistake and comes here looking for help.

---

