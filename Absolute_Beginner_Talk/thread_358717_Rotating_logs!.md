---
title: "Rotating logs!"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by dr_d on 2007-02-11
Hi. I want to have a permanent record of /var/log/aptitude which will never be deleted/rotated.

I've found a file /etc/logrotate.d/aptitude, which contains:

```

/var/log/aptitude {
  rotate 6
  monthly
  compress
  missingok
  notifempty
}

```

I've read 'man logrotate' but can't figure out what I need to change in this file to achieve the goal.

Also, is this the best way to approach this problem?

Any help would be greatly appreciated.
Cheers!

---

### Post by bapoumba on 2007-02-11
Hello,
There is a monthly /var/log/aptitude.x.gz backup file. "x" is a number, number 1 is the first logged file etc. See **man logrotate**.
Aptitude logs intented actions though. When an install or an upgrade show abnormal messages, I just save them for a while in a .txt file, so that I can go back to them if needed.

---

### Post by dr_d on 2007-02-13
Hi thanks for replying..

> When an install or an upgrade show abnormal messages, I just save them for a while in a .txt file, so that I can go back to them if needed.

That sounds like a good idea. I think I might do the same. :)

---

