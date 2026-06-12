---
title: "critical battery power warning?"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by kaston on 2007-12-12
is it possible for ubuntu to give me a warning when i'm critically low on battery power?  i have a toshiba satellite A100-VA9 and my hibernate and sleep functions don't work, so the only option i have is to make it shutdown when low on batt power.  but it would be nice to have a warning before it does it!  is this possible?

---

### Post by ronmarley1 on 2007-12-12
> **kaston said:**
> is it possible for ubuntu to give me a warning when i'm critically low on battery power?  i have a toshiba satellite A100-VA9 and my hibernate and sleep functions don't work, so the only option i have is to make it shutdown when low on batt power.  but it would be nice to have a warning before it does it!  is this possible?

I have an IBM Thinkpad R51 and it does this for me by default.  I get a message at 20 minutes, then a more dire message at 10 minutes.  When I get three short beeps, it means that I waited too long and the laptop shuts off in a few seconds.
I'll see if I can find where these messages are generated from and maybe you can enable them...

---

### Post by DutyDuty on 2007-12-12
I know if you use AWN and have the battery applet that it swells up when battery is running low.

---

### Post by kaston on 2007-12-13
> **DutyDuty said:**
> I know if you use AWN and have the battery applet that it swells up when battery is running low.what's AWN?  

basically i just want something that will sound an alarm a few minutes before it's about to shutdown.  the last time i ran out of power, it just shutdown without any warning in the middle of my work.  i can't have that happen again

---

### Post by MoToR on 2007-12-14
> **ronmarley1 said:**
> I have an IBM Thinkpad R51 and it does this for me by default.  I get a message at 20 minutes, then a more dire message at 10 minutes.  When I get three short beeps, it means that I waited too long and the laptop shuts off in a few seconds.
I'll see if I can find where these messages are generated from and maybe you can enable them...

I'll be glad to get some info as well. My IBM X20 does Hibernate and Suspend when said to (Power Button pressed, lid colsed), but doesn't do that when battery gets critical.

I've described my "wait for ubuntu to Hibernate my system" experiment it this thread: [**Battery critical shutdown not working?**]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=636885&highlight=battery+critical")

---

### Post by ronmarley1 on 2007-12-14
I've looked around and can't find where to set low battery power notices.  Right clicking on the battery icon gives a few options, but not that.
Sorry...

---

### Post by some_girl on 2007-12-16
*Bump* 
I need to know this too...  Seems like it ought to be something simple, since Ubuntu obviously knows when the battery's getting low, no reason it can't warn us before shutting down!

---

### Post by rraheja on 2008-02-06
I am having the exact same problem. I tried other suggestions of putting acpi_cpufreq in /et/modules and even tweaked the configuration editor, but does not fix the problem.

any suggestions? I have a sony vaio vgn-n130g running gutsy 7.10 / gnome-power-manager 2.2.

thx

---

### Post by rraheja on 2008-02-07
ok, so I installed KDE and its power manager gives me the warning notifications correctly and honors the threshold settings.  It also does suspend/hibernate automatically.  of course, the hibernate actually does not work and crashes....which is a separate issue, but at least I now know the problem lies with the gnome-power-manager.

---

### Post by MoToR on 2008-02-13
Hmmm....

---

### Post by dtgolder on 2008-03-21
Is there a better fix for gnome?

---

### Post by MoToR on 2008-03-23
> **dtgolder said:**
> Is there a better fix for gnome?

Let me rephrase, is there **any** fix for gnome?

---

