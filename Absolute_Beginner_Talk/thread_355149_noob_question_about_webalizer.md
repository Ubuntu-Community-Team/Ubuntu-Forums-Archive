---
title: "noob question about webalizer"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by cap10kirk on 2007-02-06
webalizer is installed on my box. I just don't know how to run it. How do i execute the program?

Thanks,
kirk

---

### Post by old_geekster on 2007-02-06
Here is a link to the website for Webalizer:

[http://www.mrunix.net/webalizer/](http://www.mrunix.net/webalizer/)

It should answer most of your questions.

Sorry that I can't answer your question since I am a newbie, but I am sure this will get you started until someone can help.

---

### Post by bikeboy on 2007-02-06
Webalizer is setup to run once a night (I think) using cron.
[http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

To see if it has set itself up in cron try this ```
ls /etc/cron.daily
```
There should be a file called webalizer.

At the set time it examines your apache logs in /var/log/apache to get information out of them. It will create an html file of the results and you can view from there. Where it puts these files is determined by the file /etc/webalizer.conf which explains the options. If you want to change something you might want to backup the file ```
sudo cp /etc/webalizer.conf /etc/webalizer.conf.bak
```

---

### Post by cap10kirk on 2007-02-06
Thanks. I actually just opened a browers and typed [www.mysite.com/stats](www.mysite.com/stats). I'm such a noob.

kirk

---

