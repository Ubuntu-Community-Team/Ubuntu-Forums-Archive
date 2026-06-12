---
title: "test server help please"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-01-02
yesterday i installed the LAMP stack so i can test some php stuff before posting on the net. Everything went very well and it works great.

I only have one question: how do i make Mysql databases? is there a control panel or something??

thanks in advance :)

---

### Post by hyper_ch on 2008-01-02
install phpmyadmin - it's in the repos

after installation, go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Upon installation you should be asked to enter a root pwd, you then "root" and the pwd supplied during installtion to login into phpmyadmin.

---

### Post by rockinlinux on 2008-01-02
ok i installed it but when i got to localhost/phpmyadmin i get a 404. also on install it never asked for a password just what i was sing and i picked apache2.

here is what i installed yesterday. i did get asked for a password then:

$ sudo aptitude install apache2
$ sudo aptitude install php5
$ sudo aptitude install mysql-server
$ sudo aptitude install php5-mysql

thanks :)

---

### Post by hyper_ch on 2008-01-02
well, you're missing quite a few things and does php run?

And I was wrong about the user during the phpmyadmin install, it should come with mysql - but you miss qutie a few things there also.

---

### Post by Samhain13 on 2008-01-02
You might also want to try the MySQL Administrator and Query Browser frontends.
They're available from the repositories. You can search for:

mysql-administrator
mysql-query-browser

---

### Post by rockinlinux on 2008-01-02
well i was testing punbb and i ran the install.php and it came up...but i did not install it becuase i could not figure out how to make a database.

what am i missing? here is the original post: [http://ubuntuforums.org/showthread.php?t=655225](http://ubuntuforums.org/showthread.php?t=655225)

ok i will install both of those, but what do they do exactly?

---

### Post by rockinlinux on 2008-01-02
hyper- Yes i entered a pasword when i installed Mysql. I am not downloading the two things that samhain said.

what other packages do i need to get?

thanks both of you for the help, i have neer set anything like this up

---

### Post by hyper_ch on 2008-01-02
fist: mysql
```

apt-get install mysql-server mysql-client libmysqlclient15-dev

```

second: apache:
```

apt-get install apache2 apache2-doc apache2-mpm-prefork apache2-utils

```

third: php:
```

apt-get install libapache2-mod-php5 php5 php5-common php5-gd php5-idn php-pear php5-imagick php5-memcache php5-mhash php5-mysql
```

fourth: phpmyadmin
```

sudo apt-get install phpmyadmin

```

That will work

---

### Post by rockinlinux on 2008-01-02
ok thanks, im downloading all it now. 

ok i got this mysql admin stuff installed but i still dont see how to make a database. The only way i have ever done it was though my hosting company with cpanel....it was really easy so im a little lost :(

---

### Post by rockinlinux on 2008-01-02
hyper...i installed all that and still get the 404

---

### Post by llamakc on 2008-01-02
> **rockinlinux said:**
> ok thanks, im downloading all it now. 

ok i got this mysql admin stuff installed but i still dont see how to make a database. The only way i have ever done it was though my hosting company with cpanel....it was really easy so im a little lost :(

```

mysql -p

```

Enter the corresponding MySQL password.

Now you'll be in the mysql shell.

```

CREATE DATABASE DBName;

```

Where DBName is the name of the database you want to create or have been instructed to create. 

Now exit the MySQL shell:

```

\q

```

---

### Post by rockinlinux on 2008-01-03
thanks for that. Is there a way to do this with a control panel though. dont get me wrong im comfrtable with the terminal but for this i would rather have a GUI.

---

### Post by hyper_ch on 2008-01-03
just get phpmyadmin installed - very simple to use.

Maybe you have a little problem with yuor configuration files... someone in the german kubuntu channel had the same problem yesterday - no apache configs were created.

Post the output of this command:

```

ls -al /etc/apache2

```

---

### Post by rockinlinux on 2008-01-03
thanks :)

home@home-laptop:~$ ls -al /etc/apache2
total 56
drwxr-xr-x   7 root root  4096 2008-01-01 13:12 .
drwxr-xr-x 125 root root 12288 2008-01-03 10:05 ..
-rw-r--r--   1 root root 10384 2007-10-05 01:42 apache2.conf
drwxr-xr-x   2 root root  4096 2008-01-02 16:12 conf.d
-rw-r--r--   1 root root   895 2007-10-05 01:42 envvars
-rw-r--r--   1 root root     0 2008-01-01 13:12 httpd.conf
drwxr-xr-x   2 root root  4096 2008-01-01 13:32 mods-available
drwxr-xr-x   2 root root  4096 2008-01-01 13:32 mods-enabled
-rw-r--r--   1 root root    59 2007-10-05 01:42 ports.conf
drwxr-xr-x   2 root root  4096 2008-01-01 13:12 sites-available
drwxr-xr-x   2 root root  4096 2008-01-01 13:12 sites-enabled

---

### Post by hyper_ch on 2008-01-03
seems you have the configs... dunno what you did, but the steps outlined by me do work.

---

### Post by rockinlinux on 2008-01-03
so what now? :(

---

### Post by rockinlinux on 2008-01-03
I did exactly what you said, i even reinstalled the phpmyadmin after i did all the apt-gets....is there anything i can do?? i really need this to work

---

### Post by rockinlinux on 2008-01-03
is there any other program besides phpmyadmin to use for this?

---

### Post by rockinlinux on 2008-01-03
any ideas? anyone?

---

### Post by rockinlinux on 2008-01-04
any help would be great...anyone??

thanks :)

---

### Post by Samhain13 on 2008-01-05
> **rockinlinux said:**
> is there any other program besides phpmyadmin to use for this?

You can, of course, try the stuff I suggested earlier.
And I do suggest them because I had trouble getting phpmyadmin working some time ago. Actually, it just stopped working for some reason and I didn't have the time to ask for a solution from the forums-- I had a very urgent need.

:)

Anyway, here are a few screenshots:

---

### Post by rockinlinux on 2008-01-06
> **Samhain13 said:**
> You can, of course, try the stuff I suggested earlier.
And I do suggest them because I had trouble getting phpmyadmin working some time ago. Actually, it just stopped working for some reason and I didn't have the time to ask for a solution from the forums-- I had a very urgent need.

:)

Anyway, here are a few screenshots:

I did download and install those programs. I just dont see where i can make a new database. Some help? 

thanks in advance :)

---

### Post by Samhain13 on 2008-01-06
In MySQL Administrator, to make a new database, go to Catalogs. It's on the left side box, and it's the last item. Upon clicking it, you get a new box at the bottom left side with the heading "Schemata" where you'll see stuff like: "information_schema", "mysql", etc.

To create a new Schema, right-click on that box (where the schemata are listed) and you'll get a tool tip that says "Refresh Schemata", "Create Schema", and "Drop Schema". You'll want to pick "Create Schema". By the way, Schema is Database in this context.

After picking "Create Schema", you'll be shown a textbox where you will put the name of your Schema/Database. After you click OK, the new Schema will be included in the list box at the bottom left. Click on it and the right part of the window will become active.

From that right part of the window, you can create/edit your tables. It's very intuitive from there on.

-------------

For editing Database content, you use MySQL Query Browser.

From Query Browser, you can also create new Schemata/Databases. The list appears to the right of the screen. You can also create/edit/remove tables from the Schemata that you have available.

---

### Post by Deived on 2008-01-08
This post really helped.  Thanks guys.  I was able to install everything and it seems to work fine.  localhost gets me an index page with www located at /var/.  MySQL works from shell as well as those MySql Admin and Query apps.
I've got a question though.  I install phpmyadmin, but how do I get to it?  It was my understanding that it's browser based, but I can't seem to find it, and phpmyadmin doesnt work as a command from the shell.  I've been doing web stuff for a while, but I'm a bit of a newb at the admin stuff.

---

### Post by hyper_ch on 2008-01-08
go to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

