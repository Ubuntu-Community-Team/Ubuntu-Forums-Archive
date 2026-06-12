---
title: "Apache document root"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by ShiningWolf on 2008-01-12
Hi all,

All documentation on Apache 2.2.4 shows that the documentroot directory is normally under  /usr/local/apache/htdocs. Under the ubuntu installation there is not even a usr/local/apache.

The documentroot is now /var/www.

Why is this?

---

### Post by Miademora on 2008-01-12
I dont know why its var but there are common standards that are getting applied to several distributions like [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)

Imagine you have a server and dont know wich webserver is installed. If you have a common path for the webroot it doesnt matter wich webserver runs. You know where to find the files. Second you usually dont have that much space in /usr. Its better for high usage servers to have the files on a separate partition. Its easier for backups, performance and overall management.

Im more used to /srv/www. Dont know where /var/www comes from.

---

### Post by amo-ej1 on 2008-01-12
/srv smells like SuSe, /var/www smells likes Red Hat ;)

---

### Post by naugiedoggie on 2008-01-12
> **ShiningWolf said:**
> Hi all,

All documentation on Apache 2.2.4 shows that the documentroot directory is normally under  /usr/local/apache/htdocs. Under the ubuntu installation there is not even a usr/local/apache.

The documentroot is now /var/www.

Why is this?

The location of many of these files and directories is arbitrary.  To some extent it depends on the Unix foundation of the distribution.  I would say there are two basic structures, SysV and BSD.  These two systems had differing directory structures and locations for important scripts (e.g., boot scripts in /etc/init.d or /etc/rc.d).  You can see this clearly illustrated in Ubuntu (/etc/init.d) and Slackware (/etc/rc.d).

There is a somewhat convoluted discussion of this issue in this thread:  [**Philosophy of Directory Structure**]("http://lists.apple.com/archives/Darwinos-users/2001/Jan/msg00118.html").

*var* is for *varying data*, according to my [**Essential System Administration**]("http://www.powells.com/biblio/4-9781565921276-10") (Aeleen Frisch).  That's the Bible if you want to get religion about it.

Thanks.

mp

---

