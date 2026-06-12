---
title: "Crontab start app in workspace 2 ?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-11-13
hi i have a crontab set up to start an app, 

How can i set up crontab so the app starts in workspace 2.?

Thanks

---

### Post by hopelessone on 2007-11-13
export DISPLAY=:1

Ahhhh Haaaa...i c...

---

### Post by jordanmthomas on 2007-11-13
I would look into devilspie, which allows you to start programs on a certain desktop (otherwise it's difficult or impossible to choose)

Also, cron is not able to start programs in X unless you tell it where to do it
See post 8 (maybe 9?) in this thread for details.
[http://ubuntuforums.org/showthread.php?t=572105](http://ubuntuforums.org/showthread.php?t=572105)

---

### Post by justleen on 2007-11-13
I'm not sure wether this is possible out-of-the-box.
You'd need something like [Devils Pie]("http://burtonini.com/blog/computers/devilspie"), to control the windows...
Or  a different window-manager..


That said, crontab is normaly used for background proccesses. To start X applications, i'd preffer the session manager..

---

### Post by jordanmthomas on 2007-11-13
Wait, you're the same guy I helped in that thread.

LOL

---

