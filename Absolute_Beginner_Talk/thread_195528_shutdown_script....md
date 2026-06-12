---
title: "shutdown script...?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by mms on 2006-06-13
I want to write a script that will automatically record a cumulative record of ubuntu's uptime over the lifetime of this install.  How can I do that?  I'm aware of the command 'uptime',  but I don't know how to write a script that will execute automatically each time I shutdown.  Any tips?

---

### Post by simonn on 2006-06-13
I can spot one problem with your approach.

Recording the uptime when you shutdown will not allow for system crashes.

The only way I can think of doing it is running a cron job that records the current uptime. This will only be as accurate to one minute, maximum.

On reboot you could check for an existing uptime file and make sure it is kept if there is one e.g. by renaming it.

When the period you want to assess the uptime for ends, you could total up the uptimes in the files and calculate it from there.

---

### Post by mms on 2006-06-13
[QUOTE=simonn]I can spot one problem with your approach.

Recording the uptime when you shutdown will not allow for system crashes.

The only way I can think of doing it is running a cron job that records the current uptime. This will only be as accurate to one minute, maximum.

On reboot you could check for an existing uptime file and make sure it is kept if there is one e.g. by renaming it.

When the period you want to assess the uptime for ends, you could total up the uptimes in the files and calculate it from there.[/QUOTE]

There's no need for it to be precisely accurate, and hopefully there won't be many crashes ;) .  But I'll look into cron.  Thanks.

---

