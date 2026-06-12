---
title: "Freshclam Problem"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by Pudwud on 2006-02-04
What does this mean and how can I solve the problem?

...freshclam
ERROR:  Can't open /var/log/clamav/freshclamlog.log in append mode (check permissions!)
ERROR:  Problem with internal logger.

Thanks.

---

### Post by bscbrit on 2006-02-04
Are you running freshclam without root permissions?  You should be using

sudo freshclam 

if you are starting it manually.  If it is being started automatically then you have a configuration error.

---

### Post by Pudwud on 2006-02-04
Thanks.

---

