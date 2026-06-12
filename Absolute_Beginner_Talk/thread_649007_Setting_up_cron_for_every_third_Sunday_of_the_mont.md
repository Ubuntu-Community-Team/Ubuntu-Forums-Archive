---
title: "Setting up cron for every third Sunday of the month"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by hfranco on 2007-12-24
I'm trying to run a backup script that runs every 3rd Sunday of the month.

Wikipedia has a pretty decent article on cron but I cannot seem to get the correct field in place for this job.

[http://en.wikipedia.org/wiki/Crontab]("http://en.wikipedia.org/wiki/Crontab")

Any clue?

---

### Post by xtacocorex on 2007-12-24
Taken from [http://forums.macosxhints.com/archive/index.php/t-25110.html](http://forums.macosxhints.com/archive/index.php/t-25110.html)
> aixccapt99
According to man 5 crontab, wday accepts values 0-7, where Sunday is either 0 or 7. So just write:
0 4 15-21 * 0 /path/to/my/command

That will run your script every month, on Sundays whose dates are between 15-21 (inclusive, ie, the third Sunday only), at 4 a.m.

[Just so everybody's clear, the reason for 15-21 is that the third Sunday is always one of those dates, and no other Sunday (2nd, 4th) can ever be those dates. ]


I would change the time (4) to whatever time you want.

Or you could look at anacron, it's available in the repos and is sort of a scheduler like cron.

---

### Post by hfranco on 2007-12-24
Thanks xtacocorex.  Hopefully this works.

---

### Post by hfranco on 2007-12-24
> wtsuka
06-25-2004, 09:59 PM
Third Sunday was the original thought, but once a month or every three or four weeks on a Sunday will suffice.

I had tested aixccpt99's method but it ran on each day of the month specified and every weekday specified.

Thanks.

From the comment above it appears it does not work.

---

### Post by xtacocorex on 2007-12-24
Crap, didn't read that far into the thread.  I'd try going the anacron route and see where that goes.  Sorry for the bad advice.

I thought there was a GUI in the repos for setting cron jobs that had some way to figure out the scheduling.  I remember using it, but I haven't run Linux for a while.

---

