---
title: "How to backup mysql and moodle folders daily"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by robinlennox on 2007-11-23
Hi all,

Just wondering if someone could help.

I have a moodle server setup on ubuntu server 6.06 with mysql.

Just wondering how i could do this using cron?

---

### Post by hyper_ch on 2007-11-23
My little HowTo will give you most answers...

just skip the SSH part...

[http://www.howtoforge.com/rsync_incremental_snapshot_backups](http://www.howtoforge.com/rsync_incremental_snapshot_backups)

There are examples how to do a mysqldump with all databases and how to make snapshot style backups with cron.

---

### Post by robinlennox on 2007-11-23
Can't see how this is meant to work if I need to run my sqlbackup for a diffrent server?

---

### Post by hyper_ch on 2007-11-23
A backup should be made to another location and that's what the howto is about. But you can rsync localy also.... rsync FROM TO --> if both is local files system then there will be locally synced...

---

### Post by robinlennox on 2007-11-23
Does rsync handle mysql?

---

### Post by hyper_ch on 2007-11-23
no, but if you read through that link then you should know how to backup mysql.

---

### Post by robinlennox on 2007-11-23
> **hyper_ch said:**
> no, but if you read through that link then you should know how to backup mysql.

Using SSH seems to be overkill if I'm wanting to backup to the same server?

---

### Post by hyper_ch on 2007-11-23
re-read my postings here...

---

### Post by robinlennox on 2007-11-23
If i skip the ssh part, I don't understand how i can backup my sql database?

Sorry for being a noob....

---

