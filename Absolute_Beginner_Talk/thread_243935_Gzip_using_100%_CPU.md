---
title: "Gzip using 100% CPU"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by EpicCrusadr on 2006-08-25
Lately I've noticed that when my computer idles, I get 100% CPU usage sometimes. The Gnome System monitor shows nothing, but when I use the command "top", I see that Gzip is using close to 100% of the CPU! The fan is roaring at full, then, after about 10 minutes the cpu usage normalizes between 0 and 5 percent and the fan stops. What would cause this? Is this normal? I'm not using Gzip at the time. I have the i686 Kernel and a Pentium M 1.86 Ghz processor in a Toshiba M55.

Thanks in advance!

---

### Post by Klaidas on 2006-08-25
I don't think I can help for the whole problem, but by saying that the fan stops, do you mean it slows down or it completely stops rotating?

---

### Post by EpicCrusadr on 2006-08-26
I think it stops. I can't hear it afterwards, and there is no air coming out of the vent, so I assume it has stopped.

---

### Post by steve.horsley on 2006-08-26
Next time, try:
> sudo ls
sudo ps -ef | grep gzip
The first one is just to prime sudo so it won't send a password prompt into grep.
The second one should tell you what the command was that launched gzip.

---

### Post by EpicCrusadr on 2006-09-01
Thanks for the advice. I'll try it next time this happens.

---

### Post by EpicCrusadr on 2006-10-06
So, it happened again recently. I did what you said, and this is the output:

anil@ubuntu:~$ sudo ps -ef | grep gzip
root     11991 11990 62 00:00 ?        00:05:32 gzip
anil     12268 12221  0 00:09 pts/0    00:00:00 grep gzip

---

### Post by nocturn on 2006-10-06
> **EpicCrusadr said:**
> So, it happened again recently. I did what you said, and this is the output:

anil@ubuntu:~$ sudo ps -ef | grep gzip
root     11991 11990 62 00:00 ?        00:05:32 gzip
anil     12268 12221  0 00:09 pts/0    00:00:00 grep gzip

OK, this can be caused by cron or something running gzip on the log files in /var/log.

But I cannot be sure about this...

Does it last long?  Are any files in /var/log getting large?

---

### Post by SonWon on 2008-07-13
This happens to me also.  Here is the output from sudo ps -ef | grep gzip

root      9288  9287 48 08:32 ?        00:03:59 gzip
sonwon    9818  9546  0 08:40 pts/1    00:00:00 grep gzip

Any ideas?

---

### Post by SonWon on 2008-07-13
Found it!

backup manager was the problem.  I installed the files but didn't know that it auto configures itself into cron/root.

SonWon

---

