---
title: "Apache2 wont die!"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by mudcow007 on 2008-04-10
hello all

im trying (in vain) to install tomcat5, it seems to have installed correctly an is running (supposedly!)

however i also have apache2 running which i dont think is a good idea. so i tried to stop apache2 by using: 

/usr/sbin/apache2 -k stop

but i got this message after i ran the command

apache2: apr_sockaddr_info_get() failed for pbx-1
apache2: Could not reliably determine the servers fully qualified domain nam, using 127.0.0.1 for ServerName

httpd (no pld file) not running

the name of the server is pbx-1

before i tried to stop apache2 i coudl see the contents of var/www but now i cant. does this mean apache2 has stopped? if so shouldnt i be able to see the var/www folder via tomcat5?

sorry for the long post

thanks

---

### Post by Thelasko on 2008-04-10
```
killall apache2
```

---

### Post by kbless7 on 2008-04-10
if that doesn't work do

```
ps -aux
```

this will bring up a list of the running programs. find apache2 and type

```
kill -9 pid
```
or 
```
kill -15 pid
```

where the pid is the process ID you get from the list

---

### Post by mmichalik on 2008-04-10
actually, the following is the correct way to stop Apache2

sudo /etc/init.d/apache2 stop

But, it will restart automatically next time you reboot the box so, you will have to remove the scripts from the init.d directory or remove Apache2 all together from your box.

Or, just stop it again, next time but, in theory, they should run together just fine.

---

### Post by spiderbatdad on 2008-04-10
> **mmichalik said:**
> actually, the following is the correct way to stop Apache2

sudo /etc/init.d/apache2 stop

But, it will restart automatically next time you reboot the box so, you will have to remove the scripts from the init.d directory or remove Apache2 all together from your box.

Or, just stop it again, next time but, in theory, they should run together just fine.

Actually...it's ```
sudo apache2ctl stop
```
Or in some older versions: sudo apachectl -k stop.
This causes the parent process to send the sigterm to all the child processes, so that you don't end up with a number of http executables still running.

---

### Post by mmichalik on 2008-04-10
the /etc/init.d/apache2 service script, by it's own definition, basically calls the apache2ctl command.  So, in essence we're both correct.

$> cat apache2
#!/bin/bash -e
#
# apache2               This init.d script is used to start apache2.
#                       It basically just calls apache2ctl.

But, I thought that it's always best to use the utility scripts in the init.d directory because they are placed there by the repository installations that use them and have all the env variables, etc already defined for the services.  Please correct me if I am wrong.

I could understand using the apache2ctl command if the web server was installed from a download from the Apache website and not a .deb package from the repository.  That makes total sense.

Is my thinking off here?

---

