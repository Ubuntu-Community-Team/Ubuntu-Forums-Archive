---
title: "Cant connect to mysql"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by chymo on 2007-04-13
Hi, I have a lamp setup in a VMware VM.  I can access this VM by it's unique IP through other computers on my LAN.  I can access phpmyadmin, for example, but I'm having issues connecting to mysql with other php apps. 

All computers of my LAN can see the apache and phpmyadmin being served from my lamp VM, meaning everything is working.  When I setup a testcon.php file on another webserver in my LAN, I am getting a "Lost Connection" error. 

<?php $link = mysql_connect('192.168.0.106','testuser','testpw'); if (!$link) { die('Could not connect to MySQL: ' . mysql_error()); } echo 'Connection OK'; mysql_close($link); ?>

Is this a DNS/hostname issue?  Or is this an issue with my lamp configuration?

Thanks.

---

### Post by compmodder26 on 2007-04-13
By default, mysql should be set up to only allow connections from localhost.  Have you changed the configuration to allow it to accept from outside?

---

### Post by az on 2007-04-13
> **chymo said:**
> Hi, I have a lamp setup in a VMware VM.  I can access this VM by it's unique IP through other computers on my LAN.  I can access phpmyadmin, for example, but I'm having issues connecting to mysql with other php apps. 

All computers of my LAN can see the apache and phpmyadmin being served from my lamp VM, meaning everything is working.  When I setup a testcon.php file on another webserver in my LAN, I am getting a "Lost Connection" error. 

<?php $link = mysql_connect('192.168.0.106','testuser','testpw'); if (!$link) { die('Could not connect to MySQL: ' . mysql_error()); } echo 'Connection OK'; mysql_close($link); ?>

Is this a DNS/hostname issue?  Or is this an issue with my lamp configuration?

Thanks.


Mysql does not listen to the network by default.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Set mysql bind address
Before you can access the database from other computers in your network, you have to change its bind address. Note that this can be a security problem, because your database can be accessed by others computers than your own. Skip this step if the applications which require mysql are running on the same machine. 

type: 

nano /etc/mysql/my.cnf
and change the line: 

bind-address           = localhost
to your own internal ip address e.g. 192.168.1.20 

bind-address           = 192.168.1.20
If you try to connect without changing the bind-address you will recieve a "Can not connect to mysql error 10061".

---

### Post by chymo on 2007-04-13
> **compmodder26 said:**
> By default, mysql should be set up to only allow connections from localhost.  Have you changed the configuration to allow it to accept from outside?

I did change the bind address to the IP displayed in ifconfig.  Is this what you are talking about?

---

### Post by compmodder26 on 2007-04-13
Yes.  You also need to make sure port 3306 is open in your firewall.

---

### Post by chymo on 2007-04-13
> **az said:**
> Mysql does not listen to the network by default.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Set mysql bind address
Before you can access the database from other computers in your network, you have to change its bind address. Note that this can be a security problem, because your database can be accessed by others computers than your own. Skip this step if the applications which require mysql are running on the same machine. 

type: 

nano /etc/mysql/my.cnf
and change the line: 

bind-address           = localhost
to your own internal ip address e.g. 192.168.1.20 

bind-address           = 192.168.1.20
If you try to connect without changing the bind-address you will recieve a "Can not connect to mysql error 10061".


Thanks, I did double check this... and I went through the guide in the community documentation.  That's why I was leaning towards a hostname issue.  There are other computers/php apps on my LAN connecting to other mysql databases using just an IP address for the hostname... so I'm thinking I should be able to get this to work...

---

### Post by chymo on 2007-04-13
> **compmodder26 said:**
> Yes.  You also need to make sure port 3306 is open in your firewall.

Is there a way I can test this?  

I will have to check on this... however this is an internal thing between LAN computers... so all IP's are 192.168  Would the port still be blocked internally?

---

### Post by compmodder26 on 2007-04-13
Also, you need to make sure the user you are trying to connect to mysql as, is allowed to connect from the machines/hosts you are trying to connect from.  This is controlled in the users table in the mysql database.

---

### Post by chymo on 2007-04-13
here is the exact error:


[I]Warning: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server during query in /path/testconn.php on line 1
Could not connect to MySQL: Lost connection to MySQL server during query[/I]

---

### Post by compmodder26 on 2007-04-13
> **chymo said:**
> Is there a way I can test this?  

I will have to check on this... however this is an internal thing between LAN computers... so all IP's are 192.168  Would the port still be blocked internally?

Did you set the firewall up?  If you didn't explicitly run any kind of setup, then the default ubuntu firewall (iptables) will have all ports open and it shouldn't be the source of your connection problems.  If this is just running on your lan and the whole lan is behind a firewall then it isn't necessary to lock the ubuntu firewall down.

---

### Post by chymo on 2007-04-13
> **compmodder26 said:**
> Did you set the firewall up?  If you didn't explicitly run any kind of setup, then the default ubuntu firewall (iptables) will have all ports open and it shouldn't be the source of your connection problems.  If this is just running on your lan and the whole lan is behind a firewall then it isn't necessary to lock the ubuntu firewall down.

Yes, everything I'm doing is behind a LAN.  So there shouldn't be any port issues.  I can ping all computers fine with responses.  They're all talking to each other... I can bring up phpmyadmin from any LAN pc... but all the content there is all local to the VM... 

I'm trying to use the VM as a test server for pre-production stuff.  and right now it looks like mysql is only working locally.  

Could it be anything with apache2 config?  (this wouldn't make sense though because it seems to be working fine)

---

### Post by chymo on 2007-04-13
> **compmodder26 said:**
> Also, you need to make sure the user you are trying to connect to mysql as, is allowed to connect from the machines/hosts you are trying to connect from.  This is controlled in the users table in the mysql database.

I played with this.  I used the default % for Any Host field.  I also typed in the IP for the host field.  I tried using a root account and a different admin account in the testcon.php file... no luck.    I know this is something simple...

I am able to log in to phpmyadmin with the user accounts I'm using in testcon.php

---

### Post by compmodder26 on 2007-04-13
The fact that you can administer it from phpmyadmin just means that it is functioning properly on the local machine.  What we need to find out is why outside machines can't connect directly to MySQL.  

Since you are securely behind a firewall in the LAN, try telneting into the server from another machine using 3306 as the port:

telnet serverhostname 3306

If you can't do that, then I'd say it's a firewall issue.

---

### Post by compmodder26 on 2007-04-13
> **chymo said:**
> I played with this.  I used the default % for Any Host field.  I also typed in the IP for the host field.  I tried using a root account and a different admin account in the testcon.php file... no luck.    I know this is something simple...

I am able to log in to phpmyadmin with the user accounts I'm using in testcon.php

I also forgot to mention that after altering the contents of the user table, you need to use the command mysql command "flush privileges" to make the changes take effect.

---

### Post by chymo on 2007-04-13
> **compmodder26 said:**
> The fact that you can administer it from phpmyadmin just means that it is functioning properly on the local machine.  What we need to find out is why outside machines can't connect directly to MySQL.  

Since you are securely behind a firewall in the LAN, try telneting into the server from another machine using 3306 as the port:

telnet serverhostname 3306

If you can't do that, then I'd say it's a firewall issue.

This is different, When I tried to telnet, I get:

M
 5.0.22-Debian_0ubuntu6.06.3-log7/kR8]OS5,OMc*DYqPy3./?

Connection to host lost.

---

### Post by compmodder26 on 2007-04-14
Something isn't right, it appears you are connecting successfully, but you aren't able to sustain a connection.  I think you may need to explicitly open port 3306 in your firewall.  Are you running a gui or just the command line (e.g. Ubuntu Desktop edition or Ubuntu server edition)?  If you are running the Desktop edition, download firestarter from the repositories and configure it to open port 3306.  If you are running the server edition (no gui) I can help you manually configure iptables to open 3306.

---

### Post by compmodder26 on 2007-04-14
I just thought of something.  You didn't by chance change the default port that MySQL listens on, did you?

---

