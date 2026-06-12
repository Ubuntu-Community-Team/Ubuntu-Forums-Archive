---
title: "Installing Lamp from CD"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by InternetDominus on 2007-11-06
Hi,

I have my ubuntu cd which I insert into cdrom and when I try to install from menu "Install Lamp Server" the setup seems to be trying to install ubuntu all over again. Setup starts asking for IP, Server name (localhost or ubuntu), etc...so I am guessing it is trying to install ubuntu again, and I stop installation. 

Is this right? Should keep installing Lamp that way or is something wrong with my cd?

Thanks,

Rom

---

### Post by Dr Small on 2007-11-06
Installing the Lamp Server also installs Ubuntu too.

---

### Post by volksman on 2007-11-06
If you just want to run a lamp type server while keeping your existing Ubuntu Desktop install I would strongly suggest the Xampp package available from [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

Otherwise if you want to build from scratch try this howto: [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by Dr Small on 2007-11-06
> **volksman said:**
> If you just want to run a lamp type server while keeping your existing Ubuntu Desktop install I would strongly suggest the Xampp package available from [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

Otherwise if you want to build from scratch try this howto: [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)
Also, check out my tutorial if you plan to install xampp.
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

---

### Post by az on 2007-11-06
> **volksman said:**
> If you just want to run a lamp type server while keeping your existing Ubuntu Desktop install I would strongly suggest the Xampp package available from [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

Otherwise if you want to build from scratch try this howto: [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

Don't use Xampp.  You will get much better support using the native LAMP stack from Ubuntu.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

To install LAMP, you don't need the cd.  Booting from the cd is for installing the OS.  You only need to install a few packages.  You just need to just the package manager.

sudo tasksel install lamp-server

---

### Post by InternetDominus on 2007-11-08
> **Dr Small said:**
> Also, check out my tutorial if you plan to install xampp.
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

I installed xampp last week, but MySql would not work from terminal, so I ended up unistalling xampp, installing ubuntu way and messing up my ubuntu config when phpmyadmin did not work.  

Well, I prefer to install xampp, and if you could please tell me how to start mysql once it is installed I will appreciate it.  I did not see anything on that on your blog.  Thanks for the tip on how to run xampp once the pc starts!

Rom

---

### Post by InternetDominus on 2007-11-08
> **az said:**
> Don't use Xampp.  You will get much better support using the native LAMP stack from Ubuntu.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

To install LAMP, you don't need the cd.  Booting from the cd is for installing the OS.  You only need to install a few packages.  You just need to just the package manager.

sudo tasksel install lamp-server


What is the diff between xampp and sudo way? Don't they both install same needed stuff i.e. mysql, apache, php5, perl, etc?  

When you say support you mean support from the server or from here?  I was not able to install phpmyadmin the first time I tried the sudo way, and gave up.  

Thanks!

Rom

---

### Post by az on 2007-11-08
> **InternetDominus said:**
> What is the diff between xampp and sudo way? Don't they both install same needed stuff i.e. mysql, apache, php5, perl, etc?  

When you say support you mean support from the server or from here?  I was not able to install phpmyadmin the first time I tried the sudo way, and gave up.  

Thanks!

Rom

Using the package manager allows you to keep your system up-to-date and get security fixes very easily - you just run

sudo apt-get upgrade 

and everything keeps working.  This is not so with xammp.

---

### Post by InternetDominus on 2007-11-08
My terminal is not recognizing tasksel command...why is that?
----------------------------------
sudo: tasksel: command not found
----------------------------------

---

### Post by az on 2007-11-09
> **InternetDominus said:**
> My terminal is not recognizing tasksel command...why is that?
----------------------------------
sudo: tasksel: command not found
----------------------------------

In Feisty, the Ubuntu base system includes Tasksel. You can either install LAMP using tasksel or install the LAMP packages as detailed above.

If you are running Dapper, you need to install Tasksel from Universe.  It's just easier to install the individual packages:

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

---

### Post by InternetDominus on 2007-11-09
Got it thanks!

---

