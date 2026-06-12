---
title: "httpd.pid and named.pid"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-02-13
I'm attempting to make a server, and can't find the httpd.pid and named.pid files requested by web-cp.

Just wondering if anyone knows where they should be, or if there's something I should have installed by now?

I'm running apache2 and bind if that helps?

---

### Post by OffAxis on 2008-02-13
pid is a process id...

is apache2 running?
```

sudo /etc/init.d/apache2 restart
```

---

### Post by OffAxis on 2008-02-13
the .pid files are kept in 
/var/run/

I don't know about httpd, but my server's .pid comes up as
/var/run/apache2.pid

hope that helps.

---

### Post by Squizz on 2008-02-13
Yeah, apache is running.  I've looked in the /var/run/ folder, and there is an apache2.pid file there.  Do you think substituting it will work?

I have to fill in the init script and pid file for the services "httpd" and "bind".

I just found named in /var/run/bind/run/named.pid though!

---

### Post by OffAxis on 2008-02-13
worth a shot, huh? :)

---

### Post by Squizz on 2008-02-13
I have a whole lot of other problems to work through, but I think that did the trick for this particular one thanks.

---

### Post by OffAxis on 2008-02-13
cool.
Never used it myself, but a lot of people also use ispconfig
[http://www.ispconfig.org/]("http://www.ispconfig.org/")

It seems to be a bit more supported than web-cp.

---

