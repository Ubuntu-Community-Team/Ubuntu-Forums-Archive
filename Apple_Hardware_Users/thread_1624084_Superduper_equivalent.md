---
title: "Superduper equivalent"
date: 2010-11-17
forum: Apple Hardware Users
---

### Post by rmcellig on 2010-11-17
On my iMac, I use Superduper to clone my drive every night to an external 250GB USB drive.Is there something similar for Ubuntu?

[Superduper]("http://www.shirt-pocket.com/SuperDuper/SuperDuperDescription.html") has saved me a couple of times and also has saved me time. One time my internal main HD crashed. All I had to do was start up from my external USB drive and I was back in action. I then used Superduper to clone back to my internal HD, rebooted and all was well again. 

I am looking for something similar in Ubuntu seeing that I am using Ubuntu about 95% of the time.

---

### Post by oswaldkelso on 2010-11-18
```
man dd
```

[http://wiki.linuxquestions.org/wiki/Dd](http://wiki.linuxquestions.org/wiki/Dd)

---

### Post by rmcellig on 2010-11-18
Isn't that what Clonezilla uses? Is thre a way for me to create a cron job using dd that runs every night at a specific time that backs up to an external USB drive where it does a complete backup first and then just incremental ones after that?

Isn't dd a very slow way to do a backup? If so is there a way to make it quicker?

I use the Scheduled Tasks application for my cron jobs.

---

### Post by oswaldkelso on 2010-11-19
Sounds like you want rsync to just back up your changes to your cloned disk, rather than re-clone the whole disk every night

[http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)

---

