---
title: "Cron Job Help"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-01-27
Hi there,

I have a script that I want to run once a week at a 2pm on Saturday.

I do know that cron is what I need to use but I have no idea what do to or what to search for, for help.

I need a way of doing this in the command line because it is for a command line system. However any information on a GUI app would be nice. On my office machine I'm using xfce.

Thanks.

---

### Post by guysmiley25 on 2007-01-29
I see there is not much interest in the subject eh?

Ok so looking around I found this

```
crontab -e
```

And then added a line like this.

```
0 14 * * 0 /home/guysmiley25/myscript.sh
```

Witch should mean that my script should run every Sunday at 2 pm. But i'm not getting the desired effect.

I'm not sure if the script is running or not. But I do know that the script works! any ideas?

---

### Post by Pobega on 2007-01-29
According to [this page](http://www.scrounge.org/linux/cron.html) shouldn't it be set as:
> 0 14 * * 6 /home/guysmiley25/myscript.shThe 0 in the end would be Sunday, not Saturday.

**Edit:** You should should be creating a file, like ~/.myscript.cron, and run it with *crontab myscript.cron*. Use *crontab -l* to see if cron is running your script, and if it's there you're safe.

---

