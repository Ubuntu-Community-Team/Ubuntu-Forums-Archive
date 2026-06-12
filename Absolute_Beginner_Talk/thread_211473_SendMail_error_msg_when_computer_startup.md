---
title: "SendMail error msg when computer startup?"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by dreamyman on 2006-07-08
*Starting basic networking
rm:cannot remove '/etc/mail/sendmail.cf' read-only system
make: **[sendmail.cf] error 1
updating auth..
/usr/share/sendmail/update-auth: line 98: cannot create temp file for here document: read-only file system

Creating /ect/mail/relay-domains
#optimal file
A forced reload
** Yur should issue '/etc/ini.d/sendmail/reload'.


what's the problem?:confused:

---

### Post by dreamyman on 2006-07-08
sorry, I have found that:



[https://launchpad.net/distros/ubuntu...ail/+bug/43752](https://launchpad.net/distros/ubuntu...ail/+bug/43752)

Maybe I should choose postfix

---

