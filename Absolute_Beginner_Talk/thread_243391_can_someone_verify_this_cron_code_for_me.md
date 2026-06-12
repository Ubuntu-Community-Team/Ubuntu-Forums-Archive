---
title: "can someone verify this cron code for me?"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Hranj on 2006-08-25
i want this task to run every weekday (mon-fri) at 10 in the morning. can someone tell me if this would be right.

```
at 09**mon-fri
```

thanks

---

### Post by amo-ej1 on 2006-08-25
According to man crontab 

```

              field          allowed values
              -----          --------------
              minute         0-59
              hour           0-23
              day of month   1-31
              month          1-12 (or names, see below)
              day of week    0-7 (0 or 7 is Sun, or use names)


```

It would result in adding
```

0 10 * * 1-5 do_some_magic.sh

```
to your crontab

---

