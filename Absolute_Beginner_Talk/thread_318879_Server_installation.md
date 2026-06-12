---
title: "Server installation"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by tkakadagreen on 2006-12-14
I've been using windows for a while now but i want to make the switch to linux, i just got my Ubuntu Cds and i can't seem to be able to install LAMP. Is there a special procedure to do that?](*,)

---

### Post by Shatrat on 2006-12-14
Maybe this will help:
[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

---

### Post by tkakadagreen on 2006-12-14
Ouch, i think i got the desktop Cd instead... Is there any hope? can i still install LAMP? would there be any performance lag?

---

### Post by PilotJLR on 2006-12-14
You can still do it, but it would be more work overall. The desktop CD will install a full graphical environment, complete with cool apps like gimp and openoffice. A server, of course, does not need these. If you don't mind bloat, then it's fine...
For a optimal server install, just download the server iso file. It will be better in the long run. Just keep in mind the server install does NOT install a graphical environment, though you can add one on after the fact fairly easily.


> **tkakadagreen said:**
> Ouch, i think i got the desktop Cd instead... Is there any hope? can i still install LAMP? would there be any performance lag?

---

### Post by az on 2006-12-14
> **tkakadagreen said:**
> Ouch, i think i got the desktop Cd instead... Is there any hope? can i still install LAMP? would there be any performance lag?

See:
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

and 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


Basically, you can install LAMP on any Ubuntu box by running:

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

There will not really be a performance loss, unless you are serving a few hunded people at the same time.  You will expose yourself to vulnerabilities by running unneccesary software.  That's why a unix server is traditionaly command-line only.

---

