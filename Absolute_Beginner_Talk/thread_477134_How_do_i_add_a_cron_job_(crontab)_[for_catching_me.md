---
title: "How do i add a cron job (crontab)? [for catching memory leaks by using Top via Cron]"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-06-18
[B]So, I saw a great tip on how to see if a program is leaking memory. I've heard stuff about firefox before and I've come back to it hoping it's gotten better. 
[/B]


[B]But I'd like to do the thing below to see if Firefox has memory leaks:
[/B]


[B]From:
[/B]
**[http://www.venturecake.com/10-linux-shell-tricks-you-dont-already-know-for-once/](http://www.venturecake.com/10-linux-shell-tricks-you-dont-already-know-for-once/)**

[B]-----start of snip--------
[/B]
**3. Catch Memory Leaks By Using Top via Cron**
Memory apps are rare in Linux, but they do happen, particularly when using beta distros or home grown software. A lot of time the identitty of the app with a memory leak isn’t that apparent. Linux has an Out-Of-Memory app built in to identify and kill these apps, but by the time it eventually kicks on your system may have been unusually slow for a while – and that’s if your patience hasn’t already worn thin and you’ve rebooted.
 The normal way to find an apps memory consumption is by running top (or one of it’s graphical equivalents, like System Monitor) and check the Resident Set Size (called Res or RSS) of the processes you care about (you can ignore figures for how much memory the app has allocated – memory leaks come from usage, not allocation, and apps can assign bucketloads of memory they don’t use without hurting your system). Most people aren’t aware top can be run non-interactively, which means you can use cron and top to generate a simple report of an apps usage over time.
 [LIST]
[*]Run **top**.
[*]Use the **<** and **>** keys until processes are sorted by RES (resident memory usage).
[*]Hit **W** to write your config out to a file
[*]Add a cron job:
[INDENT]crontab - <<< ‘*/15 * * * * top -n 1 -b’
[/INDENT][/LIST] ----end of snip------------------------------------------

**[SIZE=4]My question is: How do I add the cron job? =;=P~:icon_frown:[/SIZE]**

---

### Post by suhanduman on 2007-06-18
"sudo crontab -e"

then write your command with correct schedule.

---

