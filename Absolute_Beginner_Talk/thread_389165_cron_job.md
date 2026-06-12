---
title: "cron job?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by qpwoeiruty on 2007-03-20
I have a command that I'd like to run at the first bootup of every 4th day.

is this what I'd put in crontab or is it something else?

0 0 1-31/4 * * * command

---

### Post by qpwoeiruty on 2007-03-20
maybe it's: 0 0 */4 * * * command???

---

### Post by qpwoeiruty on 2007-03-20
anybody?

---

### Post by ardchoille42 on 2007-03-21
> **qpwoeiruty said:**
> I have a command that I'd like to run at the first bootup of every 4th day.

is this what I'd put in crontab or is it something else?

0 0 1-31/4 * * * command

You have too many asterisks in there.

# m h  dom mon dow   command

0 0 */4 * * command

That should be enough to run a command every fourth day of the month.

---

### Post by Mr. C. on 2007-03-21
See week 7 notes "Cron & Automation" to see how cron works and its crontab format:

[http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)

MrC

---

