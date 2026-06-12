---
title: "Using crontab"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-12-14
So I don't think I've ever had crontab work for me.

I've written a couple scripts here and there for organizing my hard drive and I want to run them via cron.

```
$ export EDITOR=vim && crontab -e
```

will allow me to edit my crontab.

This is what it currently looks like:
> # m h  dom mon dow   command
0       */12    *       *       *       php /home/brett/cron/organize.php
0       */4     *       *       *       /home/brett/cron/rsync.sh


For root I have:
```
# export EDITOR=vim && crontab -e
```
> # m h  dom mon dow   command
0       3    *       *       *      aptitude update && aptitude -y upgrade && aptitude autoclean

But nothing seems to work. I know that my two scripts in my personal crontab work because when I run them from the command line with the absolute paths, they do their job.

What am I doing wrong?

---

### Post by altonbr on 2007-12-14
Oh and yes, I have this line at the top of my shell script:
```
#!/bin/sh
```

---

