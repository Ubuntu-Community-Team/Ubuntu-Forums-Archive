---
title: "Drupal RSS feed not updating CRONTAB!"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by tipalm73 on 2007-05-16
I cannot get my news feeds to update automatically. I am running Feisty Fawn/MySQL/Apache2/PHP5.

I had an error in the drupal console that crontab wasnt working and to run it manually. If i put [http://mywebsite.com/drupal/cron.php](http://mywebsite.com/drupal/cron.php) in an URL the feed updates but Id like it to do this automatically every 15 mins. I have it set in drupal but my crontab looks like this:

# m h  dom mon dow   command


would  ':15:0 *** wget http://mywebsite.com/drupal/cron.php' do the trick?

Thanks in advanced.

---

### Post by Skrynesaver on 2007-05-17
Almost ;)
```

0-45/15:*** wget...

```
Starting at zero minutes pat the hour until 45 minutes past the hour, every fifteen minutes

---

### Post by tipalm73 on 2007-05-17
I ended up with:

15,30,45,59 * * * *  /usr/bin/lynx -source [http://roflcopter.com/drupal/cron.php](http://roflcopter.com/drupal/cron.php)

and it worked..well sort of 15 mins/15min/15mins/14mins. I like your code better, it give me th every 15 mins I hunger for.

thx!

---

