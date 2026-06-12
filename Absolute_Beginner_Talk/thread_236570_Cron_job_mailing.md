---
title: "Cron job mailing"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by mdecler2 on 2006-08-14
Hello,

I want to mail a file using a cron job. I don't really want the reulting output of a script, I just want to mail a flat file.

I recently used the line,
10 22 * * 1-5 mail -s "logfile for cmd" <log.file [email]mdecler2@myaddress.com[/email]

in my crontab file which did nothing.
I got a message in my /var/spool/mail, "/bin/sh mail: command not found".
Apparently I do not have mail program?
The intention was to mail the file to an external server.
Is this possible?

Any advice?

---

