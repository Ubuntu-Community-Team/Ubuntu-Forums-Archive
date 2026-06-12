---
title: "cron not running"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by adamdidthis on 2007-08-21
HI,

I am trying to run a cron job but not having much luck. I am trying to run a php page. the job looks like this:

0,5,10,15,20,25,30,35,40,45,50,55 * * * *    [http://intdev/components/com_supportcenter/addon/readmail/readmail.php?security=dB9sLmZUyuo6HZaN](http://intdev/components/com_supportcenter/addon/readmail/readmail.php?security=dB9sLmZUyuo6HZaN)

I added it useing crontab -u root -e

Any ideas?

---

### Post by ggaaron on 2007-08-21
What are you exactly trying to do? What is the wanted effect?

You can test cron for example by:
rm ~/testmycron
crontab -u root -e

*/5 * * * * touch ~/testmycron

and after some time:
ls ~/testmycron

But what do you want to do, because your cron won't do anything at all in my opinion...

---

### Post by Dr Small on 2007-08-21
To run a php file, you can not use an HTTP address, is must be a local address, meaning the file is on your machine, not somebody else's.

So, if you do infact have the file, you can use this crontab to run a php file:
```
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /path/to/php -q /htdocs/file.php
```

Example, for me, since I am running xampp, and want to run the file cron.php located under /opt/lampp/htdocs/shells/, and my php is located at /opt/lampp/bin/php here's what it would look like:
```
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /opt/lampp/bin/php -q /opt/lampp/htdocs/shells/cron.php
```


Dr Small

---

