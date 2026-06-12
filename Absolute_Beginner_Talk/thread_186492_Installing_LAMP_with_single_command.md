---
title: "Installing LAMP with single command?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by skafiskafnjak on 2006-06-02
Is there a way to install LAMP (Apache, PHP, MySQL) with a single command? 
If so will it install PHP4 or PHP5?

I use 6.06 OEM installation.

After installing LAMP is Apache started by default and where is its ROOT directory?

---

### Post by S{yndrom}e on 2006-06-02
I don't know much about LAMP or anything, but the root directory is "/".
 In "/" lies all the other folders, like usr, bin, home, etc, var and so on.

To navigate to root you can either do

cd /

in terminal

or open up the file browser and press crtl+L
and in the location field enter "/"

---

### Post by jobezone on 2006-06-02
Found this guide from ubuntu's wiki : [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by elemental666 on 2006-06-02
The easiest way I know is to got to [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html) and get their package, install it in /opt per their instructions. Worked fine on breezy, will set it up on Dapper later this morning.

---

### Post by bluefrog on 2006-06-02
If you use the server install cd, you have the choice to setup LAMP from the start.

---

### Post by hedgie on 2006-06-04
There is or will be soon according to this:
[http://ubuntu.hu/index.php?title=Dapper_Drake](http://ubuntu.hu/index.php?title=Dapper_Drake)
which says: 
The Server Edition of Ubuntu 6.06 LTS includes a unique mechanism to set up a standardized, certified, and supported LAMP (Linux, Apache, MySQL and PHP) server with a single command.

---

### Post by Noelinho on 2006-06-04
In relation to the PHP, I've never got Apache2 working with PHP5, so I use PHP4. It's probably just me though, I can't say I ever looked in to it very far.

---

### Post by adamkane on 2006-06-07
Handy-dandy single-command to install LAMP:

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
Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by dvarsam on 2006-06-08
What the heck (or wtf), guys!!!

If you have listened to "Mark Shuttlewood's" interview (taken on 30/05/2006) offered in the Ubuntu Cafe (which lasts 4 hours - could be more), you would have _heard_ the following:

There is a NEW automated way to install:

1. MySQL
2. Apache
3. PHP
4. PhpMyAdmin (I think this is included too!)

In some way, you type the word "LAMP" on a Terminal (or maybe there is a package out there) & all the above get installed AUTO-MAGICALLY!!!

I do NOT know how this works, but if "Mark S." says that this is out for the Servers, it probably _is_ & there must _also_ be a way to install this package on a Desktop Ubuntu too!!!

The question _now_ is:

DOES SOMEBODY KNOW HOW THIS IS DONE????

Thanks!

---

### Post by adamkane on 2006-06-08
I think you make a selection when you first insert your install CD.

There is still an issue that remains: "Which LAMP version do you need?" 
- Some people want the latest PHP5/MySQL5, but many LAMP frameworks require you to use MySQL4 (e.g. osCommerce), unless you want to rewrite everything for MySQL5 (ugh).

There is still another issue: "I already have Ubuntu installed. What do I do to install LAMP now?"
- See Post 8.

---

### Post by malcolmb on 2006-06-08
I used XAMPP on breezy and that baby worked perfectly.

I dont know if there are any advantages to using a bundled pack like Xampp or if it's better to just install all the services from the repositories.

---

### Post by verbatim210 on 2006-06-09
i typed copy and pasted

"sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql"

and nothing happens.

---

### Post by adamkane on 2006-06-09
XAMPP installs a huge number of apps, so you are up a creek, if you any issues to troubleshoot.

---

### Post by adamkane on 2006-06-09
verabatim:

You won't notice anything, unless you need to use LAMP for something like a database-driven website, a CMS (content management system like drupal or oscommerce), or use mysql with amarok or mythtv.

After you reboot, you can create some test databases, but it's not very interesting by itself:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by tribaal on 2006-06-09
Hum maybe the "single-line command" thing is a little misunderstood:

The server install CD has a LAMP installation item on it's menu. It will install a barebone LAMP server, without a GUI. 

In my understanding, that's what a "single line install of LAMP" is... it saves tons of time setting up a server, especially when you have several to install.

Is that what you meant?

- trib'

---

### Post by dvarsam on 2006-06-10
Dear "tribaal",

> Hum maybe the "single-line command" thing is a little misunderstood:

The server install CD has a LAMP installation item on it's menu. It will install a barebone LAMP server, without a GUI. 

In my understanding, that's what a "single line install of LAMP" is... it saves tons of time setting up a server, especially when you have several to install.

Is that what you meant?

Well, when I listened on Mark Shuttlewood's interview, I thought that somebody could install the whole:

```
sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql
```

With a single command like this:

```
 sudo apt-get install lamp
```

That is what I thought he was talking about...!!!

---

### Post by elemental666 on 2006-06-10
[QUOTE=dvarsam]
If you have listened to "Mark Shuttlewood's" interview (taken on 30/05/2006) offered in the Ubuntu Cafe (which lasts 4 hours - could be more), you would have _heard_ the following:

There is a NEW automated way to install:

1. MySQL
2. Apache
3. PHP
4. PhpMyAdmin (I think this is included too!)

In some way, you type the word "LAMP" on a Terminal (or maybe there is a package out there) & all the above get installed AUTO-MAGICALLY!!![/QUOTE]


Could you provide a link to that interview, I haven't been able to find it...

---

### Post by Mirrorball on 2006-06-10
Another piece of information for you: Apache's root directory is /var/www

---

### Post by dvarsam on 2006-06-11
[QUOTE=elemental666]Could you provide a link to that interview, I haven't been able to find it...[/QUOTE]

Sure!

[http://ubuntuforums.org/showthread.php?t=186732](http://ubuntuforums.org/showthread.php?t=186732)

Have Fun!

P.S.> You will need to sacrifice some 4 hours to listen to the full story! But it is nice & worths it!

---

### Post by kabam on 2006-06-14
[QUOTE=jobezone]Found this guide from ubuntu's wiki : [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)[/QUOTE]

Unfortunatly, this doesn't work (at least not with dapper).  The package php4 does not exist...  I'm new to ubuntu (and linux for that matter), but what I need is exactly what the guide says PHP4 and MySQL4....  Anyone know of an "eacy" way for a beginner to install this?

Thanks!

---

### Post by nigel on 2006-06-14
the packages do exist 

php4 is in universe (this is not enabled by default)

you need to enable the universe repositories in you repositories list, 
and then roberts your fathers brother

if you don't know how to enable the repositries see here
[https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu]("https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu")

---

### Post by Kilz on 2006-06-14
[QUOTE=kabam]Unfortunatly, this doesn't work (at least not with dapper).  The package php4 does not exist...  I'm new to ubuntu (and linux for that matter), but what I need is exactly what the guide says PHP4 and MySQL4....  Anyone know of an "eacy" way for a beginner to install this?

Thanks![/QUOTE]

I just finished setting up a lamp server on xubuntu with those instructions yesterday. I went with php5, there is a choice on the page. So far Im happy, the xfce desktop is speedy on my little server and I like having a gui.

---

### Post by kabam on 2006-06-15
Thanks!  I learned about the other repositories late last night...  I'm still having trouble getting everything set up the way I want, but I'm sure that most of that is just a lack of knowledge at this point.  I'm trying to create a "staging" server for my web development using Apache 1.3.*, PHP4, MySQL4, and Perl.  I've got XAMPP wokring on my Win XP development box (and on my new Ubuntu box), but I'm looking to replicate the final host environment as close as possible using Ubuntu (the actual public server is using CentOS).  So far I'm liking Ubuntu, I guess I'm just still looking for a "one-button install" since I have no experience and limited time.  

Anyway, thanks for the help....  time to get a bigger hammer :-).

---

