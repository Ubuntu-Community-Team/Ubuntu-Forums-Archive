---
title: "probably very simple proftp question"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by d.j.schroeder on 2007-03-14
I am trying to set up a proftp server on my machine.  It is installed and claims to be running.  I used the default configuration file.  My problem is no one can connect to it at all.  This is true both over the internet and within my LAN, so it shouldn't be a port forwarding problem.  Any ideas?

---

### Post by docetes on 2007-03-14
does it work locally?

---

### Post by d.j.schroeder on 2007-03-14
No it does not work locally.

Also when I restart it using sudo /etc/init.d/proftpd restart

It returns:  ProFTPd is started from inetd

I don't really know what that means or if it is normal.

---

### Post by d.j.schroeder on 2007-03-14
Ok, I figured it out.  Needed to run as ServerType standalone.

Working fine now.

---

