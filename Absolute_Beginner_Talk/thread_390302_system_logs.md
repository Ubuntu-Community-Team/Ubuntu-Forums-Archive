---
title: "system logs"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by X86 on 2007-03-21
hey peeps 

I have a question about system logs.
In System>Administration>System Log
it shows my history how do I delete thies logs?
just to clean it up a bit thanks

---

### Post by mlind on 2007-03-21
There's a cron job that automatically archives your old logs from /var/log directory. If you want to manually remove or clean up the log files System Log Viewer shows, open a terminal or file-browser and go to /var/log directory. You probably need root privileges to write for most/all of the files there.

---

### Post by X86 on 2007-03-21
That helps I got to work on it but you mentioned it does it automatically so I was just wondering....
thank you.....     ;-)

but I still like doing stuff manually so.

---

