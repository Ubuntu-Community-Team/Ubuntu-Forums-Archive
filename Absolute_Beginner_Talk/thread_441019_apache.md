---
title: "apache"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by edrad80 on 2007-05-12
Hi 

I am new to Ubuntu, finally decided to leave MS forever. Can I install apache or similar server on the Ubuntu desktop edition. I am using it on a Windows installation currently. It is a Pentium III machine

Thanks
Edward

---

### Post by bernied on 2007-05-12
```
aptitude install apache2
```
If you want php, it's an extra package or three.
You can also get the older version 1.x (1.3 I think) - just install apache instead of apache2

---

### Post by nickruiz on 2007-05-12
I, too, am new to Ubuntu (using Feisty). I have been having difficulties installing Apache 2.2. I tried installing it with the Synaptic Package manager and apt-get install apache2, but I am unable to view the welcome webpage at [http://localhost](http://localhost). At one point I had apache and apache2 installed, but removed the apache 1.3 installation.

Now that I have Apache 2.2 running, how do I get [http://localhost](http://localhost) to map to the default splash page? Thanks for your time.

Thanks,
Nick Ruiz

---

### Post by bernied on 2007-05-12
Keep in mind that it is dangerous to run a web server and not know what you are doing, though this doesn't apply if it is not open to the outside world. The default installation of apache is not meant to be the most secure and you should know what you are opening your machine up to. There is plenty of information at the [apache web site](http://httpd.apache.org/).

Having said that, some of this might help:

First, you can check whether or not apache is running, like this:
```
ps -e | grep apache
```That's show me all processes (ps) of every session (-e) then look for the word apache (grep apache). Is there a process for apache? There should be several if it is running.

If it's not running, you can start it like this:
```
sudo /etc/init.d/apache start
```This is how you start system services, not like a regular program, but this won't make it startup everytime you boot. For that you need to mess with the links in the /etc/rcX.d (where X is 0-6) directories for this, but there are easy GUI ways to do this (sysvinit editor, I think it's called). 

If it is running, you can have a look in the log files:
```
cd /var/log/apache2
ls
less <one of the files that you can see>
```The error.log file might be a good place to start looking.
(You might need to use sudo if you're not allowed to access the files)
Anything obvious?

You can also check whether the port is open using
```
sudo netstat -ltp | grep apache
```You should get at least one of these lines (though your numbers will be different):
```
# netstat -tlp | grep apache
tcp6       0      0 *:www                   *:*                     LISTEN     11145/apache2
tcp6       0      0 *:https                 *:*                     LISTEN     11145/apache2
```

Also, have you installed any firewall packages? If you're using a firewall that relies on iptables, then this will show your rules:
```
sudo iptables -L
```Have a look for the word DROP in this output.
Any other firewall programs?

---

### Post by nickruiz on 2007-05-12
Thank you for your help. Unfortunately, I am not finding much of anything with regards to apache2's status on my system. When using ps -e | grep apache, I don't find anything.

```

nickruiz@UberUbuntu:/var/log/apache2$ ps -e
.
.
.
 6567 pts/1    00:00:00 bash
 7961 pts/1    00:00:02 gksudo
 7964 ?        00:00:02 nautilus
 7967 ?        00:00:00 bonobo-activati
 7991 ?        00:00:00 mapping-daemon
18342 pts/0    00:00:00 ps
nickruiz@UberUbuntu:/var/log/apache2$ ps -e | grep apache
nickruiz@UberUbuntu:/var/log/apache2$ 

```

So then I attempted to shut down and restart apache2:

```

nickruiz@UberUbuntu:/var/log/apache2$ sudo /etc/init.d/apache2 stop
 * Stopping web server (apache2)...                                                          [ OK ] 
nickruiz@UberUbuntu:/var/log/apache2$ sudo /etc/init.d/apache2 start
nickruiz@UberUbuntu:/var/log/apache2$

```

And then tried again using the ps -e | grep apache command, but couldn't find anything. I also checked the logs, but they are all empty.
sudo netstat -ltp also didn't show me any open apache ports. I have Firestarter installed.

Any additional help would be useful. I usually have no problems with Apache on Windows, but I would dare not go back to Egypt after traveling so far....(read Exodus if you're confused =) ).

Thanks again for your help.
Nick Ruiz

---

### Post by bernied on 2007-05-12
Are you sure it's installed?
```
sudo aptitude install apache2
```
What's the output?

---

### Post by nickruiz on 2007-05-12
It appears to be installed....

```

nickruiz@UberUbuntu:/var/log/apache2$ sudo aptitude install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
nickruiz@UberUbuntu:/var/log/apache2$

```

I have tried removing all of apache2 via Synaptic Package Manager and reinstalling, but I haven't had much luck.

---

### Post by jtraub on 2007-05-12
try
```
sudo aptitude purge apache2
```
```
sudo aptitude install apache2
```

Are you using Feisty?
It seems like my old problem with Apache on Edgy

---

### Post by nickruiz on 2007-05-12
Yes, I'm using Feisty. I tried reinstalling apache2 and have included the output for the reinstallation.

```

nickruiz@UberUbuntu:/var/log/apache2$ sudo aptitude purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  apache2{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 86.0kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 112587 files and directories currently installed.)
Removing apache2 ...
nickruiz@UberUbuntu:/var/log/apache2$ sudo aptitude install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  apache2 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/38.4kB of archives. After unpacking 86.0kB will be used.
Writing extended state information... Done
Selecting previously deselected package apache2.
(Reading database ... 112585 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.3-3.2build1_all.deb) ...
Setting up apache2 (2.2.3-3.2build1) ...
nickruiz@UberUbuntu:/var/log/apache2$ 

```

Unfortunately, I still do not see any apache processes running and cannot view [http://localhost](http://localhost). Any other ideas? Thank you all for your help.

---

### Post by freebeer on 2007-05-12
ok... you've purged and re-installed it looks like.  Did you restart?

---

### Post by nickruiz on 2007-05-13
Yep...still no luck....

---

### Post by bernied on 2007-05-13
everyone scratches head...

so, just to be totally sure, you have tried to restart apache2, after the remove (purge) and the reinstall?
```
sudo /etc/init.d/apache2/start
```
Is it still the same output (ie. none)?

See if you get any enlightenment from any of the following:
```
sudo apache2ctl configtest
sudo apache2ctl status
cat /var/log/messages | grep apache
cat /var/log/syslog | grep apache
```

Anything?

And can I just say, that I have run apache on at least four different linux installs, and it has always worked perfectly - sometimes my configurations have not been perfect, but that was not apache's fault. Something very odd is happening with your install.

---

### Post by nickruiz on 2007-05-13
First, I would again like to thank you all for your help.

No, I still have no success with running apache. I entered the commands you specified.

```

nickruiz@UberUbuntu:~$ sudo /etc/init.d/apache2 start
Password:
nickruiz@UberUbuntu:~$ sudo apache2ctl configtest
apache2: Syntax error on line 189 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/httpd.conf: No such file or directory
nickruiz@UberUbuntu:~$ sudo apache2ctl status
w3m: Can't load http://localhost:80/server-status.
nickruiz@UberUbuntu:~$ cat /var/log/messages | grep apache
nickruiz@UberUbuntu:~$ cat /var/log/syslog | grep apache
nickruiz@UberUbuntu:~$ 

```

Interestingly enough, I do not seem to have an httpd.conf file within the /etc/apache2/ directory. I opened the apache2.conf file to browse the area within the config file that causes the error.

```

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf (<-- Error here)

# Include ports listing
Include /etc/apache2/ports.conf

# Include generic snippets of statements
Include /etc/apache2/conf.d/

```

I hope this provides you with more information. Apparently, one of the problems is the lack of an httpd config file, which would certainly provide enough reason for why the apache server is non-functional. The question now becomes, why didn't the installation didn't create all of the necessary config files?

---

### Post by bernied on 2007-05-13
At last, now we're getting somewhere. That is an empty file you are missing - bizarre.
You can create it just like this:
```
sudo touch /etc/apache2/httpd.conf
```
Here's the README file in /etc/apache2/
```
$ cat /etc/apache2/README
Apache2 Configuration under Debian GNU/Linux
============================================

Debian's default Apache2 installation attempts to make adding and
removing modules, virtual hosts, and extra configuration directives as
flexible is possible, in order to make automating the changes and
administering the server as easy as possible.

Files and Directories in /etc/apache2:
-------------------------------------

apache2.conf

        This is the main configuration file.

conf.d/

        Files in this directory are included by this line in
        apache2.conf:

        # Include generic snippets of statements
        Include /etc/apache2/conf.d

        This is a good place to add additional configuration
        directives.

httpd.conf

        Empty file.

```
So, I'm guessing - 
- httpd.conf has been left in for backwards compatibility
- your install was missing httpd.conf - but why?

Does it work now?

---

### Post by nickruiz on 2007-05-13
I added the file and restarted my pc. Now I entered in the following:

```

nickruiz@UberUbuntu:~$ sudo /etc/init.d/apache2/start
Password:
sudo: /etc/init.d/apache2/start: command not found
nickruiz@UberUbuntu:~$ sudo /etc/init.d/apache2 start
nickruiz@UberUbuntu:~$ sudo /etc/init.d/apache2 stop
 * Stopping web server (apache2)...                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
                                                                         [ OK ]
nickruiz@UberUbuntu:~$ sudo /etc/init.d/apache2 start
nickruiz@UberUbuntu:~$

```

Still no luck.

---

### Post by nickruiz on 2007-05-13
I don't know if this will assist in providing information, but I have the following apache packages installed:

```

nickruiz@UberUbuntu:/etc/apache2/mods-available$ dpkg -l | grep apache
rc  apache                                     1.3.34-4.1                             versatile, high-performance HTTP server
rc  apache-common                              1.3.34-4.1                             support files for all Apache webservers
rc  apache-perl                                1.3.34-4.1                             versatile, high-performance HTTP server with
ii  apache2                                    2.2.3-3.2build1                        Next generation, scalable, extendable web se
ii  apache2-doc                                2.2.3-3.2build1                        documentation for apache2
ii  apache2-mpm-prefork                        2.2.3-3.2build1                        Traditional model for Apache HTTPD 2.1
ii  apache2-utils                              2.2.3-3.2build1                        utility programs for webservers
ii  apache2.2-common                           2.2.3-3.2build1                        Next generation, scalable, extendable web se
ii  libapache2-mod-php5                        5.2.1-0ubuntu1.1                       server-side, HTML-embedded scripting languag

```

---

### Post by nickruiz on 2007-05-14
Just an update. I am still having the same issue. Please let me know if you have any further advice. Thanks for your time.

---

### Post by nickruiz on 2007-05-16
bump

---

### Post by bernied on 2007-05-16
> **bernied said:**
> See if you get any enlightenment from any of the following:
```
sudo apache2ctl configtest
sudo apache2ctl status
```

What's the output from these now?

Also, do you get anything from:
```
sudo apache2ctl start
```

(Sorry, I'm out of ideas)
Anyone else??

---

### Post by nickruiz on 2007-05-16
Thanks for bearing with me. Enclosed are my outputs:

```

nickruiz@UberUbuntu:~$ sudo apache2ctl configtest
Password:
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
Syntax OK
nickruiz@UberUbuntu:~$ sudo apache2ctl status
w3m: Can't load http://localhost:80/server-status.
nickruiz@UberUbuntu:~$ sudo apache2ctl start
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
nickruiz@UberUbuntu:~$ sudo apache2ctl status
w3m: Can't load http://localhost:80/server-status.
nickruiz@UberUbuntu:~$ 

```

I have also attempted the following:
```

nickruiz@UberUbuntu:~$ sudo apache2 -k start
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
nickruiz@UberUbuntu:~$ sudo apache2 -k restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd not running, trying to start
nickruiz@UberUbuntu:~$ 

```

It looks like there might be some issue with "httpd", of which I am not familiar.

---

### Post by bernied on 2007-05-16
httpd is http daemon - I think it's the old name of the main apache server daemon, which seems to be called apache2 now.

Maybe you'd do well to shut up its other complaint about the domain name as well, even if you just call it localhost.

This is in /etc/apache2/apache2.conf near the top:
```
ServerName localhost:80
```

Just a thought, have you completely purged the earlier apache version? Like jtraub suggested for the apache2 re-install?

---

### Post by nickruiz on 2007-05-16
I may have mucked things up further. I completely removed apache and reinstalled apache2. Now I get the following problem:

```

 root@UberUbuntu:~# apache2 -k start
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs
root@UberUbuntu:~# apache2 -k restart
httpd not running, trying to start
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
no listening sockets available, shutting down
Unable to open logs

```

I may try completely removing apache2 also and starting from scratch. I'll let you know how that goes.

---

### Post by nickruiz on 2007-05-16
Unfortunately, I am still having the same problem, even after removing and reinstalling apache2. I had thought that the problem could have been with the Ubuntu Feisty CD that was used to install apache2, but it appears that I am having the same problem after downloading the apache2 modules from the internet. I'm running out of ideas...:(

I attempted to change my ports.conf to listen on ports 88 and 448 (instead of 80 and 443), but I did not have any luck.
```

root@UberUbuntu:~# apache2 -k start
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:88
no listening sockets available, shutting down
Unable to open logs
root@UberUbuntu:~# 

```

An additional question...I have noticed on some forum threads a reference to the /usr/local/apache2 directory. I do not seem to have such a directory.

---

### Post by nickruiz on 2007-05-16
Aha! It appears that I had multiple references to Port 80 in my ports.conf file. It appears that I can view [http://localhost](http://localhost) now. Sorry for the problem, guys. Thank you all for your help. Hopefully this is a closed issue now.

---

### Post by bernied on 2007-05-17
Hooray! Well done.

So, that message:
```
(98)Address already in use: make_sock: could not bind to address 127.0.0.1:80
```was the key?
But you didn't get that message until quite late in this thread, so there must have been something else, even after the missing httpd.conf file. Perhaps it was the use of the 127.0.1.1 address for localhost?

I still find this weird, especially that there were so few error messages to be found. But, as they say, if it works don't fix it.

---

### Post by nickruiz on 2007-05-19
I swear, Apache hates me. I'm back to square one again, somehow. I haven't made any configuration changes, aside from attempting to installing php via apt-get, yet the next time I restarted my laptop, I find myself unable to view [http://localhost](http://localhost).

Here's what I researched:
```

root@UberUbuntu:~# apache2ctl status
w3m: Can't load http://localhost:80/server-status.
root@UberUbuntu:~# apache2ctl configtest
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
Syntax OK
root@UberUbuntu:~# netstat -lnp | grep '0.0.0.0:80'
root@UberUbuntu:~# cat /var/log/syslog | grep apache
root@UberUbuntu:~# /etc/init.d/apache2 force-reload
root@UberUbuntu:~# /etc/init.d/apache2 start
root@UberUbuntu:~# /etc/init.d/apache2 stop
 * Stopping web server (apache2)...                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
                                                                         [ OK ]
root@UberUbuntu:~# /etc/init.d/apache2 start
root@UberUbuntu:~# 

```

My apache configuration info:
```
root@UberUbuntu:~# apache2 -v
Server version: Apache/2.2.3
Server built:   Jan 15 2007 18:14:50
root@UberUbuntu:~# apache2 -V
Server version: Apache/2.2.3
Server built:   Jan 15 2007 18:14:50
Server's Module Magic Number: 20051115:3
Server loaded:  APR 1.2.7, APR-Util 1.2.7
Compiled using: APR 1.2.7, APR-Util 1.2.7
Architecture:   32-bit
Server MPM:     Prefork
  threaded:     no
    forked:     yes (variable process count)
Server compiled with....
 -D APACHE_MPM_DIR="server/mpm/prefork"
 -D APR_HAS_SENDFILE
 -D APR_HAS_MMAP
 -D APR_HAVE_IPV6 (IPv4-mapped addresses enabled)
 -D APR_USE_SYSVSEM_SERIALIZE
 -D APR_USE_PTHREAD_SERIALIZE
 -D SINGLE_LISTEN_UNSERIALIZED_ACCEPT
 -D APR_HAS_OTHER_CHILD
 -D AP_HAVE_RELIABLE_PIPED_LOGS
 -D DYNAMIC_MODULE_LIMIT=128
 -D HTTPD_ROOT=""
 -D SUEXEC_BIN="/usr/lib/apache2/suexec"
 -D DEFAULT_PIDLOG="/var/run/apache2.pid"
 -D DEFAULT_SCOREBOARD="logs/apache_runtime_status"
 -D DEFAULT_LOCKFILE="/var/run/apache2/accept.lock"
 -D DEFAULT_ERRORLOG="logs/error_log"
 -D AP_TYPES_CONFIG_FILE="/etc/apache2/mime.types"
 -D SERVER_CONFIG_FILE="/etc/apache2/apache2.conf"

```

---

### Post by nickruiz on 2007-05-19
I found this error in my error log:

```

[Sat May 19 01:42:20 2007] [error] (2)No such file or directory: Cannot create SSLMutex with file `/var/run/apache2/ssl_mutex'
Configuration Failed

```

Any ideas how to resolve this problem? It appears that Apache2 is failing to start due to this issue. I do not have a /var/run/apache2/ directory.

---

### Post by nickruiz on 2007-05-19
Thanks for bearing with me as I seem to be answering some of these questions myself. I disabled the ssl module using a2dismod ssl and now the apache2 server is running.

---

### Post by lindsay_keir on 2007-06-11
I had the same problem and got it fixed.
 [FONT="Courier New"]sudo a2dismod ssl[/FONT]  **Thank you nickruiz**
**and**
[FONT="Courier New"] /etc/apache2/ports.conf
 # Listen 443[/FONT] which is the SSL listening port.
Using Webmin Bootup and Shutdown ...
[LIST]
[*]I discovered that there was an Apache and Apache2 started
[/LIST]
[LIST]
[*]I stopped and disabled the Apache item
[/LIST]
[LIST]
[*]Started the Apache2 item - There was a complaint; but Webmin showed Apache2 did start. I then stopped and started Apache2 - both worked OK
[/LIST]
I then did a reboot, and everything is great! So I removed  [FONT="Courier New"]/etc/init.d/apache[/FONT] - which had comments saying it was Apache 1.3 - :oops:I don't know where it came from, I'm kicking a server from Dapper to Feisty.

](*,)TIP: Keep the existing settings - especially Postgresql. Feisty deleted Version 8.1 and iinstalled version - 8.2 Do not delete 8.1 - you need it to convert the 8.1 databases to version 8.2 (I had to install 8.1 to do the conversion).

---

### Post by dragonfixed on 2007-11-20
I am running it on a IBM M PRO with  2  p3  procs and the machine is running a desktop and several servers on it ans also apache 2

---

### Post by Dr Small on 2007-11-20
This method has worked 100% of the time for me:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

---

