---
title: "Is Apache, PHp and MySQL installed Correctly."
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-06-29
How do i knw\ow they are installed correctly.
How do i use them.

Where do i put my PHP files.

How do i execute them.

How do i run phpmyadmin (i have installe dit also)

I tried to run apache but got this.

```

avinash@avinash:~$ sudo /usr/sbin/apache2ctl start
Syntax error on line 101 of /etc/apache2/apache2.conf:
Invalid command 'avinash', perhaps mis-spelled or defined by a module not included in the server configuration
avinash@avinash:~$

```

---

### Post by Maggot on 2006-06-29
Not sure what you did but on line 101 of /etc/apache2/apache2.conf there is the word(s) avinash. Look at the line using nano or gedit or whatever you wish. You have to be root to modify the file.

sudo nano /etc/apache2/apache2.conf

---

### Post by hardfire_avk on 2006-06-29
[QUOTE=Maggot]Not sure what you did but on line 101 of /etc/apache2/apache2.conf there is the word(s) avinash. Look at the line using nano or gedit or whatever you wish. You have to be root to modify the file.

sudo nano /etc/apache2/apache2.conf[/QUOTE]


Ya there is something like this.

```

in each server process
# MaxRequestsPerChild .. maximum  number of connections per server process (then it dies)
<IfModule perchild.c>
NumServers           5
StartThreads         5
MinSpareThreads      5
MaxSpareThreads     10
MaxThreadsPerChild  20
MaxRequestsPerChild  0
AcceptMutex fcntl
</IfModule>
[B]
avinash www-data[/B]
Group www-data

# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"


```

The bold part is line 101.

Got it but what do i have to do with it.

---

### Post by Maggot on 2006-06-29
delete avinash www-data line completely

---

### Post by hardfire_avk on 2006-06-29
Ya there was no problem this time. But how do i run all the there pHP, APACHE and MySQL at the same time. What about PHPmyAdmin

---

### Post by hardfire_avk on 2006-06-30
Hey!! Guys. PLease help me. PLease reply to this post. Got to get somw answer.

---

### Post by cjssmo on 2006-06-30
ok to see if phpmyadmin is working open your browser and point it to you phpmyadmin in other words

[http://my.server.address/phpmyadmin](http://my.server.address/phpmyadmin)

that should get you to myphpadmin page I think the default username is admin with no password.  This will also let you know if  apache is installed and running correctly.  

If you used the ubuntu server cd apache, mysql, and php should already be installed and configured correctly.  Place any php script you have in /var/www and make sure that they have read write permissions.  Hope this helps

To execute you php script

[http://my.server.address/my.php.script](http://my.server.address/my.php.script)

---

### Post by hardfire_avk on 2006-07-03
[QUOTE=cjssmo]ok to see if phpmyadmin is working open your browser and point it to you phpmyadmin in other words

[http://**my.server.address/**phpmyadmin](http://**my.server.address/**phpmyadmin)

that should get you to myphpadmin page I think the default username is admin with no password.  This will also let you know if  apache is installed and running correctly.  

If you used the ubuntu server cd apache, mysql, and php should already be installed and configured correctly.  Place any php script you have in /var/www and make sure that they have read write permissions.  Hope this helps

To execute you php script

[http://my.server.address/my.php.script](http://my.server.address/my.php.script)[/QUOTE]

what does my.server.address in the above url mean??

when i openend the same URL. It said **my.server.address not found**.

---

### Post by hardfire_avk on 2006-07-03
PLease REPLY!!!!

---

### Post by Moonshine on 2006-07-03
[QUOTE=hardfire_avk]what does my.server.address in the above url mean??

when i openend the same URL. It said **my.server.address not found**.[/QUOTE]

my.server.address = your internal IP address... might look like 192.168.0.100 or something like that...Or localhost may work. 

So the address would look like


[http://192.168.0.100/phpmyadmin](http://192.168.0.100/phpmyadmin) or
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by hardfire_avk on 2006-07-03
[QUOTE=Moonshine]my.server.address = your internal IP address... might look like 192.168.0.100 or something like that...Or localhost may work. 

So the address would look like


[http://192.168.0.100/phpmyadmin](http://192.168.0.100/phpmyadmin) or
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)[/QUOTE]
Localhost didin't work.

Will **192.168.0.100** work for me.
Or How do i get my IP ?

---

### Post by Moonshine on 2006-07-03
[QUOTE=hardfire_avk]Localhost didin't work.

Will **192.168.0.100** work for me.
Or How do i get my IP ?[/QUOTE]

If localhost doesn't work, and you're on the machine that you installed it on, I doubt its installed correctly.

If you type ifconfig into the terminal, you should get an  "inet addr:" somewhere.

But by the sounds of it, im not sure if that would work...Keep in mind that I'm not entirely sure what I'm doing either 8-[ so I don't think I can be of much more assistance

---

### Post by az on 2006-07-03
[QUOTE=hardfire_avk]Localhost didin't work.

Will **192.168.0.100** work for me.
Or How do i get my IP ?[/QUOTE]
You can always try 127.0.0.1 

That is the loopback device and always points to you.

Type 

ifconfig
to find out your ip address.

But localhost/phpmyadmin in firefox should work.

---

### Post by hardfire_avk on 2006-07-03
[QUOTE=azz]You can always try 127.0.0.1 

That is the loopback device and always points to you.

Type 

ifconfig
to find out your ip address.

But localhost/phpmyadmin in firefox should work.[/QUOTE]


localhost/phpmyadmin didn't work. Neither the IP thing.

I tried with my IP address and nothing came there. just it said NOT FOUND.

My IP also didn't work. What do i do now??

---

### Post by NewbieNik on 2006-07-09
hardfire, lets start from the beginning.

You obviously have apache installed due to the config file being there, but try installing it again to check. open a terminal window and type:-

suo apt-get install apache

Have you installed MySQL and PHP? If so can you describe how? If you are not sure go to your package manager and search for MySQL and look for MySQL server, check that it is selected, check the version number.
Now scroll down to php-mysql and ensure that is selected.
Next search for php and look for php wit hteh same version number as your MySQL server and ensure that and phpmyadmin are checked. Click OK and the system should install them.

Your apache config file did contain "avinesh www-data" this should have read "user www-data"

Check apache is running by opening firefox and typing localhost in the address bar. You should get the apache test page. If not try typing 127.0.0.1 in the address bar. This is your computers "internal" IP addess. If this shows nothing then your apache web-server is not running.

try these steps and come back to let us know your results.

---

