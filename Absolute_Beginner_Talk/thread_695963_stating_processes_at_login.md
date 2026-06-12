---
title: "stating processes at login"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Geran on 2008-02-13
hi,

I hope this is fairly simple issue... If I want to run a command as soon as my ltsp client logs in, where would I put it? I am running Edubuntu version 7.10.

For example, when user A logs in, activate "gedit"

when user B logs in, activate "student-control-panel".

Cheers,

G

---

### Post by Thelasko on 2008-02-13
[Cronjob]("https://help.ubuntu.com/community/CronHowto")

---

### Post by Geran on 2008-02-13
So what would be the setting to activate it at logon?

---

### Post by ajgreeny on 2008-02-13
Go to System>Preferences>Sessions and in the startup tab add the launcher for the program command there to run in a terminal.  The only possible problem would be if it was a root only program, when you would need to give a password before it would run, though there are ways around that as well.  Regrettably I don't remember what is needed for that, but it is certainly possible to set that action as needing no password by a particular user, ie yourself.

---

### Post by Thelasko on 2008-02-13
Sorry, Ubuntu needs to do a better job writing those instructions.  [Try this.]("http://www.debianhelp.co.uk/crontab.htm")

---

### Post by Thelasko on 2008-02-13
What ajgreeny said.

---

