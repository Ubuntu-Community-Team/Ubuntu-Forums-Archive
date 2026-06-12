---
title: "Ubuntu Housekeeping ... required ?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Dcox on 2007-05-02
Guys,

been running Ubuntu for over 2 weeks now. I noticed some log files building up ... is it necesary to build in some system housekeeping in the crontab ? Free space by deleting log/tmp files ? Any smart ideas which could be done in the cron ?

Loving the product by the way :) :)

---

### Post by viciouslime on 2007-05-02
I think all of the logs have a maximum size, so no, not really necessary :D

---

### Post by starcraft.man on 2007-05-02
Not to my knowledge, I don't think log files take up that much space... How much space did you give the Ubuntu Root folder? Long as it has spare room I don't see a reason to delete simple log files to free space.

---

### Post by compmodder26 on 2007-05-02
Linux has a little program called logrotate that will take care of log file maintenance.  It will rotate the logs every so often.

---

### Post by az on 2007-05-02
The log files get gzipped periodically.

The only maintenance you need to do is to keep up-to-date with security updates.

---

### Post by Ianman on 2007-05-02
> **az said:**
> The log files get gzipped periodically.

The only maintenance you need to do is to keep up-to-date with security updates.

and even that happens pretty much automatically ;)

---

### Post by Dcox on 2007-05-02
So really guys, nothing to do ? ubuntu works by itself! 
Thanks for the explanation!

---

### Post by cliv on 2007-05-02
Not something im used to either, what a relief \\:D/

---

