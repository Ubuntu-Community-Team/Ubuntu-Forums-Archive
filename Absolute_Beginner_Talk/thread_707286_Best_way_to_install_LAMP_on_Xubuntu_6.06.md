---
title: "Best way to install LAMP on Xubuntu 6.06?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-02-25
So I was using Ubuntu Server 6.06,
and using the command line through SSH was kind of slow,
so i'd prefer to use a system with a GUI even if it has security risks and is slower.
(My websites aren't that important)

So what would be the best Verion(s) of LAMP to install,
and what would be the best way of doing so, so that it will work right off the bat like the Server Install Version?

Or should I go the other way around and install Xfce on an Ubuntu Server installation?

---

### Post by justleen on 2008-02-25
i just install the packages needed..

sudo apt-get install mysql-server-5.0 apache2 php5-common php5 php5-mysql libapache2-mod-php5 phpmyadmin mysql-client

not sure if you would define that as a LAMP server, but in my opinion it is..

if you need more admin tools to GUI-fy it, i'd install those through apt as well

---

