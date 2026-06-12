---
title: "Slew of little problems - FF, phpmyadmin, desktop and more"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by bardic on 2007-11-12
Hey all. 
I have several questions and didn't want to make a new thread since they are all rather small problems I think. 

1) Firefox - When I am browsing a Javascript heavy site, I find it lags. Such as gReader. This is a bug or a setting on my behalf?
2) I install php, mysql and phpmyadmin but I have no idea how to start phpmyadmin. I do a bit of development and this would be of great help.
3) When into ubuntu, my desktop will show, then disappear, somethings for almost 15-20 seconds. Compiz problem?
4) When try to logout or restart, I click on the button to bring up my options and it will take upwards of 20-30 seconds to open. 

Any help on any of these problems would be great. Thanks in advance for your time and help.

---

### Post by houstonbofh on 2007-11-12
1) Probably something on your end.  However, we are guessing based on the detail provided.  Open a thread on this alone and include all the system specs.  There are some FF specific tweaks available.
2) If you installed them with apt-get, attitude, or synaptic, they are already started.
3) Could be.  Could be other hardware, resources, drivers.  Same instructions for #1 above.  However, you could combine these, as they **may** be related.
4) With 1 and 3 above it is sounding like hardware constraints.  Want to tell us what you have for a system?  CPU, hard drive size, memory and graphics card would help a lot.

---

### Post by bardic on 2007-11-13
AMD 64 3200+
Nvida GeForce 6600 LE
110 GB hdd
1 gig ram

And, I wasn't clear on phpmyadmin. I have LAMP running, but I don't know how to access the phpmyadmin. What would I type into the url to get to it?

Thanks.

---

### Post by houstonbofh on 2007-11-13
[http://127.0.0.1/phpmyadmin/](http://127.0.0.1/phpmyadmin/)

And make sure you are using nvidia-glx-new for the best performance.

---

### Post by bardic on 2007-11-13
Hey,
I tried that for phpmyadmin, but it doesn't work. I get :

> Not Found

The requested URL /phpmyadmin/ was not found on this server.
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at 127.0.0.1 Port 80

PHP is running and i can see my phpmyadmin files..

Here's the [guide]("http://www.howtoforge.com/ubuntu_lamp_for_newbies") I followed.. is there sometime wrong with the guide or did I screw things up good?

---

### Post by Dr Small on 2007-11-13
> **bardic said:**
> Hey,
I tried that for phpmyadmin, but it doesn't work. I get :



PHP is running and i can see my phpmyadmin files..

Here's the [guide]("http://www.howtoforge.com/ubuntu_lamp_for_newbies") I followed.. is there sometime wrong with the guide or did I screw things up good?
Greetings, please take a look at my guide on Apache:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

---

### Post by bardic on 2007-11-13
Thanks for the guide Dr.Smalls. 
Now, before I try it, one quick question: Whats the easiest way to uninstall apache, php, mysql and phpmyadmin?

---

### Post by mysticrider92 on 2007-11-13
Try [http://localhost/phpmyadmin](http://localhost/phpmyadmin), I don't know if it will make a difference though. I can't remember exactly how phpmyadmin worked when I set up a file server, but the address should work.

[edit] > sudo apt-get remove apache2 php5 mysql phpmyadmin should work fine for removing the programs.

---

### Post by houstonbofh on 2007-11-14
From this page... [https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)

To remove the LAMP stack remove the following packages:

apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

To also remove the debconf data, use the purge option when removing. To get rid of any configurations you may have made to apache, manually remove the /etc/apache2 directory once the packages have been removed.

---

