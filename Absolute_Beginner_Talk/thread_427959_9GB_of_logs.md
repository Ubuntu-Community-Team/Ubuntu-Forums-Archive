---
title: "9GB of logs"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-04-29
I somehow massed 9 GB of logs in /var/log. Turns out the major culprits are kern.log, kern.log.0, messages, messages.0, syslog, and syslog.0. Is it okay to delete these? why were they amassed to this size in the first place?

---

### Post by [S|G] on 2007-04-29
You probably have some sort of problem going on your machine. Did you take a look at the logs? There are problably some hints about what is going on. Anyway, you can safely delete the log files for now, but I'd really recommend looking into them first.

---

### Post by mevets on 2007-04-29
I would but vi and gedit crash when trying to view them.

Also, maybe this is just me but, did the css for this forum just disappear? wherever I go there is no css? Firebug lists 11 errors but not a missing css file.

---

### Post by Michaelt74 on 2007-04-29
I had a similar (irritating) problem a while back. Did you run a backup? If so, what it doesn't tell you is that the backup uses huge amounts of space, Check out this post, maybe it will help.

[http://opensourceroolz.wordpress.com/2007/02/01/backing-up-and-the-driver-space-eater/](http://opensourceroolz.wordpress.com/2007/02/01/backing-up-and-the-driver-space-eater/)

Good luck!

---

### Post by mevets on 2007-04-29
No, didnt backup. CSS is back though.

---

### Post by [S|G] on 2007-04-29
Try this to see if you can find anything interesting in your logs:
```
tail -n20 /var/log/logname
```
That should show you the last 20 lines of the log (you can increase the number of lines if you want)

---

