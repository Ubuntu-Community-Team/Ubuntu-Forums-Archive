---
title: "Email events and logs"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-07-26
I have set-up dansguardian and fail2ban on my system and have them logging on attempts to view banned pages and on blocking attempted logins through SSH respectively.

What I would like to do I have logged events emailed through a ISP email server to an email address.

How would I set up my system to to this?

---

### Post by kidders on 2007-07-27
Hi there,

There are lots and lots of ways of doing this sort of thing. One basic example might be something along these lines, to pick out the relevant bits of your system logs...```
grep 'something' /var/log/syslog | mail ushills@server.com
```You could perhaps add something like it to your logrotate tasks, to stop log messages falling through the cracks between rotations.

---

