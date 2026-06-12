---
title: "Writing logon scripts for complete N00bz"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by maltomario on 2008-02-13
Hello all.  I just installed kubuntu 7.10 (gutsy gibbons) recently and am plunging in head first to the whole linux thing.  So far I'm learning quite a bit but I had a quick question whose answer I haven't been able to find easily.  :confused:

I would like to basically run a certain program (gmail notifier) auto-magically after I log in and kubuntu finishes booting.  I guess this process would be the same with any other program so hopefully other kubunt-noobz in my situation might find this topic useful.  I picked gmail notifier as a starting point since I do use it regularly

Can someone point me to a tutorial on how to write a script so that I can achieve this?  Or, just spell it out in noob speak if you have time or inclination.

Thanks in advance.
-malto

---

### Post by Thelasko on 2008-02-13
It's called a [Cronjob]("https://help.ubuntu.com/community/CronHowto").

---

### Post by maltomario on 2008-02-13
thanks.  I have read that site but it doesn't mention how to write scripts, just to schedule a certain program at a certain time/day/month.  Also, it doesn't seem to have an option to specify running  a program immediately following a successful logon.  

any other suggestions?

---

### Post by maltomario on 2008-02-14
bump.

---

### Post by Thelasko on 2008-02-15
Sorry about that.  The simplest solution is to go to System>Preferences>Sessions and enter it there.  It can't run as root though.  Also, to get cron to run at startup use the [@reboot]("http://www.debianhelp.co.uk/crontab.htm") command.

---

### Post by maltomario on 2008-02-15
Thanks, i will give that a try and report back.

---

### Post by maltomario on 2008-02-15
I'm running kubuntu 7.10 - there is no "System>Preferences>Sessions" path.  Is there an equivalent menu tree for kubuntu?

---

### Post by Thelasko on 2008-02-15
That I don't know.  You can still try the cron option though.  It is GUI independent but trickier to use.

---

