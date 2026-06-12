---
title: "VERY annoying PPTPconfig problem"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by jadanzzy on 2006-01-12
I'm a newbie^max. bare with me. 

did all that was instructed in accordance to the pptpconfig. 

i added, 
[B]
deb [http://quozl.netrek.org/pptp/](http://quozl.netrek.org/pptp/) pptpconfig/
deb [http://quozl.netrek.org/pptp/](http://quozl.netrek.org/pptp/) php-gtk/[/B]

but i get,
[B]
[http://quozl.netrek.org/pptp/php-gtk/Packages.gz:](http://quozl.netrek.org/pptp/php-gtk/Packages.gz:) 404 Not Found[/B]

and,
[B]
W: Couldn't stat source package list [http://quozl.netrek.org](http://quozl.netrek.org) php-gtk/ Packages (/var/lib/apt/lists/quozl.netrek.org_pptp_php-gtk_Packages) - stat (2 No such file or directory)
[/B]
when i run sudo apt-get install pptpconfig, this is what i get:

[B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

save me.

Dan

---

### Post by milstead on 2006-01-12
Some possibilities:

1. Your network is down. Try
```
ping www.google.com
```
and
```
ping 66.102.9.104
```
in a terminal to check. I have no idea whether you are posting from your machine or not so forgive me if this sounds stupid! If the first does not work but the second does you have a nameserver problem, e.g. /etc/resolv.conf is blank. If neither work then you are not getting a line to the outside world.

2. You are using another package manager like kpackage or synaptic at the same time - you must quit them first.

3. Something else!

Timie Milie.

---

### Post by jadanzzy on 2006-01-12
thanks!

i actually got pptp to load and run, but now this problem occurs. 

Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/2
LCP: timeout sending Config-Requests
Connection terminated.
Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/3
tcflush failed: Bad file descriptor

any thoughts?

dan

---

