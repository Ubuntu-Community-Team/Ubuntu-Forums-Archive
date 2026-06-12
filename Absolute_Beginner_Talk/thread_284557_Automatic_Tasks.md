---
title: "Automatic Tasks?"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Chiaro on 2006-10-25
I was wondering...since my ISP changes my IP now and then, I want Ubuntu to update my IP for DynDNS every 6 hours.

So, basically, I'd like it to run this task in the terminal:

```
sudo sh /etc/ppp/ip-up.d/dyndns_update.sh

```

How could I get Ubuntu to perform the task by itself every six hours? Windows 98 had this feature; so I'm guessing Ubuntu should.

---

### Post by dbd on 2006-10-25
I think what you need to use is cron:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

