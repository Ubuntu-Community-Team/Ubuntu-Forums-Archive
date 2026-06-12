---
title: "hangs on apt-get while stopping a server"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by zb200 on 2007-12-17
Hello,

Installing mysql server 

sudo apt-get -y install mysql-server-5.0 
read build package etc

displays no error or notice but at last :
Setting up mysql server 5 
*Stopping mysqld

hangs on, and does nothing even if no running mysqld process after ctrl-c it breaks returns to command prompt

Does similar while  while installing php5 
sudo apt-get -fy install php5
...
**stopping web server apache2 

Tried a lot of thing removing newly installing  apache, mysql etc but no success.
things like that as well :
dpkg -configure -a
apt-get update
apt-get upgrade

thats the problem
Thanks in advance, 
zb200

---

### Post by brunetteredhead on 2007-12-17
What happens if you stop the services it hangs on manually before trying to install?

Just in case you don't know how to do this it's:

sudo /etc/init.d/[service to stop] stop

---

