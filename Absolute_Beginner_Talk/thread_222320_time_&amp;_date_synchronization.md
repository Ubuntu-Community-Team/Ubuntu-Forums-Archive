---
title: "time &amp; date synchronization"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2006-07-24
What determines when and how long between points that Ubuntu performs a synchronization of the system time & date ?

Thanks.

---

### Post by mlind on 2006-07-24
Dapper installs package called ntpdate by default, which I think synchronizes with timeserver only when "network interface is brought up", see /etc/network/if-up.d/ntpdate
It doesn't seem to be running as a cron job.

Another choice would be to install ntp package which installs a daemon that does the synchronization periodically.

---

### Post by wpshooter on 2006-07-25
I thought that the time was adjusted on a regular basis, thus the word **PERIODICALLY** on the time and date screen, is that not correct.

Are you saying the periodically means only when you make a connection to the internet.  To me that does not really ring true since if you are on a broadband constant connection, you are in effect always connected to internet.

Thus my question is what is periodically and if and how that period can be adjusted ?

Thanks.

---

### Post by mlind on 2006-07-25
> **wpshooter said:**
> I thought that the time was adjusted on a regular basis, thus the word **PERIODICALLY** on the time and date screen, is that not correct.

Are you saying the periodically means only when you make a connection to the internet.  To me that does not really ring true since if you are on a broadband constant connection, you are in effect always connected to internet.

Thus my question is what is periodically and if and how that period can be adjusted ?

Thanks.

If you need synchronization more often, either make a cronjob for ntpdate or install package called **ntp** and configure it to check time from timeserver on certain intervals.

manual pages contain often good information about the subject
```

man ntpdate

```

---

### Post by wpshooter on 2006-07-25
Thanks, I will check it out.

---

### Post by bobpaul on 2007-01-05
> **wpshooter]I thought that the time was adjusted on a regular basis, thus the word PERIODICALLY on the time and date screen, is that not correct.

Are you saying the periodically means only when you make a connection to the internet. To me that does not really ring true since if you are on a broadband constant connection, you are in effect always connected to internet.[/quote]

[QUOTE=mlind said:**
> If you need synchronization more often, either make a cronjob for ntpdate or install package called **ntp** and configure it to check time from timeserver on certain intervals.

This is an issue for me, as well. When I enabled in the periodic synchronization option in the time and date gui options, ubuntu automatically installed ntp. From wpshooter's comments, he has done this as well.

From what I can tell, ntpd, at least auto configured through the GUI, has been broken in Ubuntu since at least Breezy. My system almost always drifts to about 20 minutes fast over a 24 hour period and then seems to remain there whether I have periodically synch on or off, but is perfect if I click the manual sync button.

I did an hourly cron job like mlind suggested almost a year ago as a quick fix, but I just checked today and it's still a problem.

Does anyone have a real solution to this issue? Are others experiencing this issue? I've tried selecting different servers in the gui and that hasn't seemed to make a difference either...

---

