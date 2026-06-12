---
title: "cron job running at wrong time"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2007-06-27
Hi, 

Ive setup a "nightly" cron job to backup my media... cron daily is set to run at 4am but the backup runs at 7:30am (that is the time i saved the job)

I noted that it started soon after i put the job in the cron.daily directory.

how cah i force it to run at 4am as per crcontab?

heres the entry

25 4	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

cheers

c.

---

### Post by Yoooder on 2007-06-27
Have you checked that your machine's time is accurate?  Just out of curiousity...

---

### Post by cnschulz on 2007-06-28
yes, its running ntp and time is correct. even checked UTC vs local time

might have something to do with anacron? not sure how that works in conjunction with cron

cheers

c.

---

