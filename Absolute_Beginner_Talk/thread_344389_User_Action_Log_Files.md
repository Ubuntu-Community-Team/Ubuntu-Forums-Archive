---
title: "User Action Log Files"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by th3gh05t on 2007-01-22
Hi,

I was wondering where the 'User Action Log Files' stored. I am sure that this is not the exact name of files. But they would be the files where it stores all of the actions taken by a particular user.

Do you know what I mean?

Thanks for you time!

th3gh05t

---

### Post by dbbolton on 2007-01-22
maybe in the /var folder

---

### Post by chalex on 2007-01-22
In general, log files go in /var/log.  They are put there by a program called syslog, which is configured by /etc/syslog.conf  They are rotated by logrotate, see /etc/logrotate.conf

If you want to keep track of the commands users are running, you can install the package "acct" and read the associated documentation.  That program will log what commands are run, by whom, and when.

You could also look in the bash history file for a given user.  it's in /home/username/.bash_history and it's accessible through the "history" command which is a built-in in the shell (assuming you're using bash).

---

