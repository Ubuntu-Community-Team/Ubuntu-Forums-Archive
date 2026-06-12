---
title: "Have to start all over again"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Paradoxed on 2006-09-18
Whilst setting up Joomla which required apache mysql and php, I messed something up. When I go to [http://localhost](http://localhost)  I get this message.

Unable to connect
Firefox can't establish a connection to the server at localhost.

Where to from here?

---

### Post by buffy^ on 2006-09-18
OK untill you have a webserver up and running on your local machine your not likely to get any more than that.

---

### Post by Paradoxed on 2006-09-18
mmmm..I have already used

sudo apt-get install mysql-server

and had a look for apache which I found in

/etc/mysql

but i see that there are only to files there namely

debian.cnf (which has a x in a red box) and the other file is

debian-start.dpkg-dist

---

### Post by Brunellus on 2006-09-18
Joomla is presuming a full LAMP setup. have a look at this howto:

[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

---

