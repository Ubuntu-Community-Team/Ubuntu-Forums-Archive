---
title: "Cron- help, so confused"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by seepage87 on 2008-01-14
Please help me.  I've been reading up on cron, but I'm still not sure on the whole thing.

My understanding is that anything I put in /etc/cron.d/ will run according to the crontab style layout.

My goal is to run Deluge at 1:00am but stop at 6:00pm on weekdays and 2:00am and stop at 9:30am.  This is what I have:
```

#Weekdays
* 1 * * 1-5 alex /usr/bin/deluge
* 18 * * 1-5  root pkill deluge
#Weekends
* 2 * * 6-7 alex /usr/bin/deluge
30 9 * * 6-7  root pkill deluge

```

I'm not sure about the pkill for two reasons.  One, there has to be a more graceful way to stop deluge from the command line.  Two, I'm not sure it will work with cron, I might need the whole pathname, which I don't know.

I'm also not sure about this whole loading crontabs.  Do I need to run *crontab /etc/cron.d/deluge* or will every file like that I put in cron.d run without needing to load it?

---

### Post by seepage87 on 2008-01-15
I read [this]("http://www.pantz.org/software/cron/croninfo.html") and it said that the crontabs I put in /etc/cron.d need the user argument (like /etc/crontab) but this doesn't seem to be the case.  Can someone confirm this?

---

### Post by seepage87 on 2008-01-15
After much testing I figured out what I was doing.  The reason the file wasn't taking a user argument was because I was loading it as the crontab for a particular user.  This crontab wouldn't care where it was, and I just happened to be putting it in a directory where other crontab-like files reside.

I'm not sure why the guys I was sticking there weren't working properly before.  I probably had them formatted improperly or something, or didn't restart cron if I needed to.  It's also worth noting that if you want to start a gui application (e.g. deluge) you need to add env DISPLAY=0. to have it forwarded to the desktop display.

Turns out I didn't even need to do this since deluge (after 0.5.6.1 I think) has a built in scheduler.  I grabbed the newest package from their website and installed it instead of the one from the repositories and was good to go.

For the future I still don't know how to gracefully kill a program (i.e. not pkill as root)

---

