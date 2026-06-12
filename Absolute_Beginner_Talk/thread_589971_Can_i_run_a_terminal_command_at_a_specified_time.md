---
title: "Can i run a terminal command at a specified time?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by SmokingGun on 2007-10-24
I want to run hellanzb at 01:00 in the moring as i get free download quota at that time until 06:00.  Obviously i don't want to have to wait up each time i have stuff to download, so was wondering if there is any way of running it at a specified time? ala scheduled tasks in Windows.

---

### Post by Dr Small on 2007-10-24
Yes, it is called crontabs in Linux.
```
man crontab
```

---

### Post by steve.horsley on 2007-10-24
**crontab** for regular, periodic tasks. **at** for one-off delayed tasks.
e.g.
at teatime do-dometing-handy

---

### Post by devilears on 2007-10-25
an example of what should be in your crontab:

# ### Create combined HTML report at 09h55 and mail the links for info everyday except Sundays and Mondays
55 9 * * 2,3,4,5,6      /home/devillj/redhat_files/report_combiner2.sh 1>/dev/null 2>&1

---

