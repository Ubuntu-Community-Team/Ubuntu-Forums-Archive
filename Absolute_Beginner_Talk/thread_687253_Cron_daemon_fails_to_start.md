---
title: "Cron daemon fails to start"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by applegrew on 2008-02-04
Since yesterday I have been trying to run a php script (directly using its Cli), but it fails to run at all. It runs when run manually though.:(

Below is my crontab's content.
```
0 0,11,19 * * * /opt/lampp/bin/php -q "/home/apple/myScripts/iflickrDown.php"
```

If I copy the above command and run it from terminal manually then it runs perfectly, but in cron job it simply doesn't work!

I tried the following command, then.

```
ps aux | grep crond
```

The output I got was
```
apple     10342  0.0  0.1   2976   740 pts/5    R+   15:12   0:00 grep crond
```

So, it seems that crond (cron daemon) is not running. Hence, I tried,
```
sudo /etc/init.d/cron start
```

But I get,
```
 * Starting periodic command scheduler crond               [fail]
```

I am at my wit's end. Pls help.:confused: ](*,)

---

### Post by applegrew on 2008-02-04
**An Update:**
Just now I noticed that in Ubuntu cron daemon is amed cron and not crond. Anyway, then cron daemon is running, but still my job is not running. :(

---

### Post by hyper_ch on 2008-02-04
do you have php5-cli installed?

---

### Post by applegrew on 2008-02-04
> **hyper_ch said:**
> do you have php5-cli installed?
Yes ofcourse. Actually I haven't installed it from the repo but from another package and it is installed at /opt/lampp/bin (I have given explicit path to php as can be seen in the crontab above).

Futhermore copying and pasting the exact command from the crontab executes the script perfectly.

---

