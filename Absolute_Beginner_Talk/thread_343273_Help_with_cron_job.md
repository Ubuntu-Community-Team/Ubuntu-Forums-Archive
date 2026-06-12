---
title: "Help with cron job"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Ic3y on 2007-01-21
Hey guys 
I have a script and I was just wondering if there was anyway that I can get this script to run in cron job

the script is tick.sh and I was wanting it to run every 30 secs is there anyone who could tell me how to do this as I am unaware of how to use cron d or cron job.

Would be much appreciated
Ic3y :biggrin:

---

### Post by Hanzerik on 2007-01-21
sudo gedit /etc/crontab

Add a line like:
```

* * * * * root /path/to/tick.sh > /dev/null

```
NOTE: This will run tick.sh every minute of every day.

---

### Post by Hanzerik on 2007-01-21
Oh, how long does tick.sh take to run? If it takes a while then you will need to adjust the cron job to allow enough time to finish.

---

### Post by Ic3y on 2007-01-21
Thanks for that Hanzerik gave it a try is there anyway that you would know of that would allow me to run it every 30 secs if not I thank you for all your effort and it gives me a leg to stand on so that I can modify it.

Thanks
Ic3y :biggrin:

---

### Post by Ic3y on 2007-01-21
In reply to your previous message on how long it takes the tick.sh takes only 1-2 secs to execute

Thanks again
Ic3y :biggrin:

---

