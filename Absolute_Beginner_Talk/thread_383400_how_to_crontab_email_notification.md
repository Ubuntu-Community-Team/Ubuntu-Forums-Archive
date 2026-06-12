---
title: "how to crontab email notification"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by americaonlan.com on 2007-03-13
I am having a problem with cron and would like it to email me the error. I have read that this can be done by editing /etc/crontab and adding the following:

```
MAILTO=admin
```

My question is how to I check the email that it produces? Where is it located and how do I access it? 

Thanks a lot for any insight.

---

### Post by apjone on 2007-03-13
When a job runs via cron it sends an email to the owner unless its directed to /dev/null. Is it a single script or the whole of cron that has a problem

---

### Post by americaonlan.com on 2007-03-13
Apjone, 
Thanks a lot for the information. Do you know how I would check for the email? What file would I check?

Thanks again.

---

