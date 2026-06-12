---
title: "Samba testparm failure"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Gamebeavis on 2006-07-14
I am trying to get my Kubuntu laptop to talk to my network. But smb keeps failing when I try. I ran testparm and this is what I get.

beavis@beavislaptop:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
testparm: gconv_db.c:232: __gconv_release_step: Assertion `step->__end_fct == ((void *)0)' failed.
Aborted
beavis@beavislaptop:~$

Should I try unistalling/reinstalling samba?

---

