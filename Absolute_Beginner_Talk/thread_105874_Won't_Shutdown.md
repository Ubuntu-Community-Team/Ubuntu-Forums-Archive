---
title: "Won't Shutdown"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by qiemem on 2005-12-19
This doesn't happen consistently, maybe, a third of the time I try to turn of my computer, but it doesn't shut all the way down. It tries to terminate all sorts of processes, fails on some, and gives me a prompt that ends with "#" instead of "$" (excuse my newbieness). So I try "sudo shutdown now" and same thing happens, no matter how many times I do it. 

Sorry I can't report on which processes fail to terminate: I believe something like kernel log and some midi thing, like timidi or something. Plus some others. I'll write them down next time it happens.

I can't say this for certain, but it seems to happen only when I've had to ctrl+alt+bckspc during while it was on, and only then when that doesn't work. 

Oh ya, second part of the problem. Ctrl+alt+bckspv sometimes doesn't work, so I usually just ctrl+alt+f1 and startx. What would be causing this though? I know someone else asked about this, but the finals guys reponse didn't apply to me, I don't have any ATI cards. And is this related?

Sorry about the limited information. Just let me know what else you need. Thanks in advnace!

---

### Post by bscbrit on 2005-12-19
Next time it happens, reboot and then run the following at a command line

cat /var/log/syslog | more

By looking at the times, you should be able to find the events that occurred.  When your computer restarts it will issue a line similar to the following:

Dec 19 17:50:18 localhost syslogd 1.4.1#17ubuntu3: restart.

so the instructions immediately prior this line will be the system shutting down.  The last few might give you a clue to what it was getting stuck on.  It doesn't matter how long you wait between it locking up and rebooting - if you just want to close it down and come back to it the day after it won't make any difference, in fact the timings will show you the shutdown even more clearly.

Instead of 'shutdown', try 'sudo poweroff' and see if that works any better.

Alternatively, as soon as it dumps you into the # prompt, type 'cat /var/log/syslog | more' and you should be able to see what happened while the shutdown was taking place.

---

