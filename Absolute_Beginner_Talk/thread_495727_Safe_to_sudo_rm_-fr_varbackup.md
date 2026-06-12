---
title: "Safe to sudo rm -fr /var/backup ?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Old Pink on 2007-07-08
Hi there,

Just post this in beginner section because it's a quickie, and pretty obvious, just looking for reassurance really. ;) 

Is it safe to delete /var/backup? 

I've never put anything in there, or ran anything that works in there knowingly, and now there's a file in there called files.tgz (an archive) that is 15GB and taking too long to open.

I figure it's a complete backup of my system, which I have no need for, especially not on the same hard drive. 

Good to go? :)

---

### Post by Old Pink on 2007-07-08
Created 21st November 2006?

I must've done it and thought nothing of it. Strange I've never noticed it before. Think I can safely remove it. :)

---

### Post by taurus on 2007-07-08
Yes, it's safe to remove those *.tar.gz in /var/backup.  If you don't want the system to make a backup copy of your machine, you need to look in /etc/cron.daily or /etc/cron.weekly because it's executed by cron.

---

