---
title: "How do I tell what caused a crash?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Roman27 on 2006-10-28
My computer has been mysteriously locking up or completely crashing and rebooting all by iteslf.  How can I tell what's causing the crashes and lockups?  I have looked through /var/log/messages, auth.log, kern.log, dmesg, debug, acpid, and /var/log/gdm/0.log.  I can't find any problems in those logfiles that indicate a crash or lockup.

---

### Post by TheWizzard on 2006-10-28
that's totally weird!
sounds like a hardware problem or kernel oops. 
do you when the problem started? was it after a kernel update? do you have the same problem if you load with another kernel?
you can also run the memtest for about 2 hours to see if there's something wrong with your ram.

---

### Post by Roman27 on 2006-11-01
Grrr...  This morning I heard the distinct beep of my computer restarting at around 4:45am.  I got up to check and both my and my wife's computer had restarted.  Also, the clock on our microwave was reset.  Ubuntu might not be responsible for the "rebooting all by itself" problem.  I'm still wondering about the mysterious lockups though.  Maybe it's the result of being ungracefully shut down?

---

### Post by Ben Sprinkle on 2006-11-01
```
My computer has been mysteriously locking up or completely crashing and rebooting all by iteslf.
```
Windows computer does this all the time, I have found the cause is dirt and dust clog in your fans and cpu.
If you have a air compressor, take open your cover and blow the crap out of everything. If you don't, take fans and cpu's out and wash them with a damp but not wet cloth.

After you have done that the problem should be fixed.

---

### Post by jkvv_1973 on 2006-11-01
> **Roman27 said:**
> My computer has been mysteriously locking up or completely crashing and rebooting all by iteslf.  How can I tell what's causing the crashes and lockups?  I have looked through /var/log/messages, auth.log, kern.log, dmesg, debug, acpid, and /var/log/gdm/0.log.  I can't find any problems in those logfiles that indicate a crash or lockup.


sounds like your cpu is overheating---get your vacuum cleaner and suck the dirt out of your processor fan or buy compressed air

---

### Post by Ben Sprinkle on 2006-11-01
That's what I just said....

---

### Post by raqball on 2006-11-01
Yes it could be the CPU overheating but could also be caused by a harware issue. Does it lock up/reboot when you are doing a specific task?

---

### Post by ibuntutoo on 2007-03-15
I have the same problem. It keeps locking up, but mine will sometimes lock during the boot up. I will try to use compressed air to clean the cpu fan, since many of the locks happen when I leave the computer up from prolonged periods of time. That still does not explain the locks during boot, any sugestions. Do you think it is kernel or hardware?

---

### Post by MrKlean on 2007-03-15
Just a thought.  If your and your wifes computer are doing it, look at where their plugged in!  A power strip or an outlet going, an over loaded circuit.  I doubt both cpu's are over heating at the same time.  That would be highly unusual ; )

---

