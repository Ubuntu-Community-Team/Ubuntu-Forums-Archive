---
title: "Apache2 installed but localhost wont connect"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by hartnady on 2006-01-27
Here's a question...

I installed Apache2. It's running as a system service. This is evident because when I click **SYSTEM -> ADMINISTRATION -> SERVICES **on the menu bar in UBUNTU, its **there** and checked.

When I type sudo **apache2 -k start **I get an error: Command not found.

When I type **sudo /etc/init.d/apache2 start** at the console, nothing happens - but at least there is no error.

When I type** [http://localhost](http://localhost) **in FireFox, it says** cannot connect.**

**/var/www **is there, with one directory and some default files in it (apache-default).

What's going on? Why won't the damn web server start? How? When? Who? Why? What? Where?

Any suggestions would be very much appreciated.

Thank you.

---

### Post by bscbrit on 2006-01-27
When you type 

sudo /etc/init.d/apache2 start

do you even get asked for your password?  If not, then perhaps it is not trying to start it for some reason.

Does it show in the list of your programs when you run 'top' on the command line?

---

### Post by ardchoille on 2006-01-27
[QUOTE=hartnady]Here's a question...

I installed Apache2. It's running as a system service. This is evident because when I click **SYSTEM -> ADMINISTRATION -> SERVICES **on the menu bar in UBUNTU, its **there** and checked.

When I type sudo **apache2 -k start **I get an error: Command not found.

When I type **sudo /etc/init.d/apache2 start** at the console, nothing happens - but at least there is no error.

When I type** [http://localhost](http://localhost) **in FireFox, it says** cannot connect.**

**/var/www **is there, with one directory and some default files in it (apache-default).

What's going on? Why won't the damn web server start? How? When? Who? Why? What? Where?

Any suggestions would be very much appreciated.

Thank you.[/QUOTE]
The proper commads are:

To start apache :
sudo /usr/sbin/apache2ctl start

To stop it, use :
sudo /usr/sbin/apache2ctl stop

Finally, to restart it, use :
sudo /usr/sbin/apache2ctl restart

---

### Post by lreyes6 on 2006-01-27
how did u install it? with aptitude or synaptics?

if u do a ```
:~$ ls /etc/init.d/
``` is there apache2? apache? apache2ctl?

depending on this u start apache like this

```
:~$ sudo /etc/init.d/apache??? start | restart | stop | reload 
```

---

### Post by hartnady on 2006-01-28
Yes of course sudo asks for password.

Apache not listed in top.

**mark@MARK:~$ sudo /usr/sbin/apache2ctl start**
/usr/sbin/apache2ctl: line 80: /usr/sbin/apache2: No such file or directory
**mark@MARK:~$ ls -al /etc/init.d/apache**
ls: /etc/init.d/apache: No such file or directory
**mark@MARK:~$ ls -al /etc/init.d/apache2**
-rwxr-xr-x  1 root root 4430 2005-10-04 08:52 [COLOR="SeaGreen"]/etc/init.d/apache2[/COLOR]

---

### Post by bscbrit on 2006-01-28
> .....Debian's package installer, will disable Apache 2 by default by setting NO_START=1 in the configuration file /etc/default/apache2. To change this, edit /etc/apache2/ports.conf to change the port that Apache 2 will monitor for requests. Change Listen 80 to Listen 8080, or whatever port you want to use for testing purposes, as long as it doesn't conflict with another service. Then you can change the NO_START entry in /etc/default/apache2 to 0, and run /etc/init.d/apache2 start to start your shiny new Apache 2 Web server.

Does this help - can you check the contents of /etc/default/apache2 please ?

---

### Post by hartnady on 2006-01-30
I just reinstalled it in the end. Works fine now.

It could have been an apache / apache2 conflict.

Thanks anyways for help.

---

### Post by bscbrit on 2006-01-30
Glad that you solved your problem - even if the solution required drastic measures!

---

