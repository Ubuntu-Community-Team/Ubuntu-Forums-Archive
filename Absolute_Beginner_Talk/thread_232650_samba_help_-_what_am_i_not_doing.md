---
title: "samba help - what am i not doing"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2006-08-09
been running samba under fedora for about a month.... loaded up ubuntu because it runs coldfusion 7 so nicely...

i cant get samba working... i can see my ubuntu box, i can see the shares but i cannot login...



security = user
or 
security = share
 (both options fail)


[tmp]
comment = temp space
path = /tmp
read only = no
public = yes
browseable = yes

set up user with smbpasswd -a
restarted samba

??what am i doing wrong??

pls help....

very happy with the OS otherwise btw... very cool

---

### Post by kaffelars on 2006-08-09
The user(s) must also have the sufficient rights on the shared folder itself, have you checked this?

Haven't used Samba on Ubuntu though, only FreeBSD/PC-BSD. I had a similar problem there, but I could see the shares, but not change anything in them.

---

