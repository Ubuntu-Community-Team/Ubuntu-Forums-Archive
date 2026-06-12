---
title: "bash scripting"
date: 2012-04-01
forum: Any Other OS
---

### Post by g2kmobile on 2012-04-01
Hi all, I've been running Zorin os 5 on a IBM Thinkpad X40 for about a month. 

I kept getting warnings that the root filesystem was full (I know enough to know I wasn't causing this). Further research uncovered that this is a known problem with Ubuntu 11.10 (which Zorin os 5 is based on). 

The offending problem is (in my particular case) /var/log/ keeps getting filled with junk files and such. 

I made a batch script to simply delete the /log folder and then create a new /var/log/ directory. My script uses sudo to delete/make these folders. 

Now I want to have this script run at startup BUT I don't want to have to enter my password when it runs. 

So my question is: How do I get this script to run at startup without needing to open a terminal, execute the script, enter my password, close terminal? 

Please  note if I do all that arduous work my script works beautifully. I've tried messing with the permissions of the script, editing the sudoers file, etc,etc, nothing works.

Any help in this matter will be greatly appreciated.

---

### Post by howefield on 2012-04-01
Thread moved to "*Other OS/Distro Talk*" forum.

---

### Post by r-senior on 2012-04-01
Just rewinding a little, the standard way of avoiding log file buildup is to configure logrotate appropriately. 

Logrotate takes log files and "rotates" them, i.e. archives the active one to a compressed version and creates a new empty one. The compressed versions are kept for a configurable number of iterations.

The settings are in /etc/logrotate.conf and the manual page can be found using: ```
man logrotate
``` 

The logrotate job runs via cron on a daily basis (you should find a logrotate link in /etc/cron.daily).

As long as you have a decent sized partition with /var/log on it, logrotate should take care of your old logs. If it's not doing so, it could be misconfigured or not running, e.g. it's not set up to run with cron or cron is not running properly.

However ... you have written a script and you probably want to use it. ;)

The easiest way to do this IMO, is to mimic what logrotate does. Make your script owned by root and make a symbolic link to it in /etc/cron.daily. Make sure it has owner execute permission too:

```
$ chown root.root <your script>
$ chmod 700 <your script>
$ ln -s <your script> /etc/cron/daily/
```

Your distribution probably uses anacron for cron jobs, which means that even if your machine is not switched on when the cron job is due, it should be picked up on startup.

Obviously, if a problem with cron is preventing logrotate from running, you'd need to fix that to get your script to run. But then you might not need the script anyway?

---

### Post by g2kmobile on 2012-04-07
Thank you [r-senior]("http://ubuntuforums.org/member.php?u=288993"). I will check into this as soon as I get a chance. 

I didn't understand what logroatate does so I figured I needed my own script. 

There seems to be some pretty major breaks in functionality with ubuntu based distros, on this particular machine. 

I'll keep everybody posted on how it goes.
[[COLOR=#d40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=186490")
Sorry about posting in the wrong place, thank you howefield for moving it to the correct place.

---

