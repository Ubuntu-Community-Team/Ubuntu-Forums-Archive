---
title: "How to create sql database on LAMP"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by 74heaven on 2007-08-13
I am trying to install Joomla on my LAMP server; to my understanding I need a database for Joomla, so how I create one for it?



Sorry I have no clue what I am doing.

---

### Post by janipewter on 2007-08-13
If you're running a httpd such as apache2, my best recommendation would be to use [phpMyAdmin](http://www.phpmyadmin.net/home_page/index.php).

---

### Post by 74heaven on 2007-08-13
> **janipewter said:**
> If you're running a httpd such as apache2, my best recommendation would be to use [phpMyAdmin](http://www.phpmyadmin.net/home_page/index.php).

Thank you for the quick reply!

I have to say I tried to download it with apt-get and it didn't work...

---

### Post by janipewter on 2007-08-13
What was the issue? I use phpMyAdmin on multiple servers running Debian/Ubuntu and they all work fine.

If you are running a LAMP install and you get phpMyAdmin from the apt repo, you should have no problem.

---

### Post by 74heaven on 2007-08-13
> **janipewter said:**
> 
If you are running a LAMP install and you get phpMyAdmin from the apt repo, you should have no problem.

I have LAMP with a GUI on it, when I type in phpmyadmin with apt-get I am not even getting a single result.

---

### Post by proalan on 2007-08-13
try

1.```
sudo apt-get update
```then for apache, php and mysql 

do
2.```
sudo apt-get install apache2 mysql-server lib**apache**2-mod-auth-mysql php5-mysql
```
or```
sudo tasksel install lamp-server
```

then for phpmyadmin
3.```
phpmyadmin
```by default mysql is set up with username = root and no password
consult this guide for more information
[https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29]("https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29")

Can you post what errors if any of the steps that dont work?

---

### Post by janipewter on 2007-08-13
> **proalan said:**
> then for apache, php and mysql do
```
sudo apt-get install apache2 mysql-server lib**apache**2-mod-auth-mysql php5-mysql
```


I thought most, if not all of those packages were included with the LAMP install by default.

---

### Post by annda on 2007-08-13
> **74heaven said:**
> I have LAMP with a GUI on it, when I type in phpmyadmin with apt-get I am not even getting a single result.

what kind of gui do you have?

in order to install phpMyAdmin you need to type this in the terminal:
```

sudo apt-get install phpmyadmin
```

once it's installed, go to this uri in your browser: [http://localhost/phpMyAdmin/](http://localhost/phpMyAdmin/)

---

### Post by proalan on 2007-08-13
> **janipewter said:**
> I thought most, if not all of those packages were included with the LAMP install by default.

yes they are, according to the ubuntu guide wiki (I've not read it in a while)
> [LIST]
[*]Feisty has made a LAMP server installation a one-click process. If you are installing from an Ubuntu Server disk, you will be given the option of installing a LAMP server during intial installation. No other steps are required.[/LIST][LIST]
[*]If you have not installed a LAMP server during installation, it can be installed from Synaptic Package Manager as a package. No other steps are required.[/LIST]

---

