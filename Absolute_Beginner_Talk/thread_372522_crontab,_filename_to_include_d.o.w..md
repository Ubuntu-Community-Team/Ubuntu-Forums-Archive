---
title: "crontab, filename to include d.o.w."
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Sgurd on 2007-02-28
I created a cron entry to do a mysqldump, and it ran fine.

# m h  dom mon dow   command
0 0  * * mon,tue,wed,thu,fri   mysqldump mydb > /root/mysqldumps/$(date).mysql

but when I tried to change the date format:

# m h  dom mon dow   command
0 0  * * mon,tue,wed,thu,fri   mysqldump mydb > /root/mysqldumps/$(date +"%a").mysql

no file is generated.

How do I get the process to create 'mon.mysql, tue.mysql', etc.?

the /root/mysqldumps directory exists.

I've done all the work as root.

I've tried logging out and staying logged in to see if it runs.

   Thanks for any help - JD

---

### Post by LotsOfPhil on 2007-02-28
It works for me if you escape the + and the %
```

* * * * * touch /sandbox/1.$(date \+\%a)

```

---

### Post by Snowday on 2008-05-26
You have no idea how long it took me to get my crontab working, and all it was was the lack of escape on the special characters.

I feel so stupid that I did not figure it out faster!

Thank you! Thank you! Thank you!

---

