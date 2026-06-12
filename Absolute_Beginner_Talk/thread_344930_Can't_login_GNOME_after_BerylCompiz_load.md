---
title: "Can't login GNOME after Beryl/Compiz load"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Chachee on 2007-01-23
I loaded Beryl with the following instructions - 

[http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)

There were no problems during install

Worked fine for a few days.  Locked up once, and I decided to load into GNOME for a little while.  Well no go.

I get the login screen, it loads, get to desktop.  Monitor then flashes, I got command line login and back to the GDM login screen.  I have to try logging in about four times, and then it works.

I would like to stop doing this obviously.  I did all the commands on the instruction page backwards.  Removed the start up scripts and un-installed most of the software.  I also disabeld the repos.

My Syslog has - 

JJan 23 22:00:28 localhost gconfd (jeremy-5104): starting (version 2.14.0), pid 5104 user 'jeremy'
Jan 23 22:00:28 localhost gconfd (jeremy-5104): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 23 22:00:28 localhost gconfd (jeremy-5104): Resolved address "xml:readwrite:/home/jeremy/.gconf" to a writable configuration source at position 1
Jan 23 22:00:28 localhost gconfd (jeremy-5104): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 23 22:00:28 localhost gconfd (jeremy-5104): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 23 22:00:28 localhost gconfd (jeremy-5104): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 23 22:00:31 localhost ntpd[4868]: kernel time sync enabled 0001
Jan 23 22:00:33 localhost gconfd (jeremy-5104): Resolved address "xml:readwrite:/home/jeremy/.gconf" to a writable configuration source at position 0
Jan 23 22:00:40 localhost gconfd (jeremy-5104): Received signal 15, shutting down cleanly
Jan 23 22:00:41 localhost gdm[4657]: Error reinitilizing server
Jan 23 22:00:41 localhost gconfd (jeremy-5104): Exiting

Thanks for any help..

JT

---

### Post by Chachee on 2007-01-23
Ok,
  Apparently it's just Gnome's problem.  It even occurs when I load default.  But after 2 tries default will login.  I don't have this problem if I try to login to XFCE though.

Help please.

JT

---

