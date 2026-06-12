---
title: "Need help with dovecot - it appears not all files were installed."
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by SimbaSpirit on 2008-02-22
Alright I don't see anything relevant to this in similar threads, not does the dovecot wiki seem to cover this.

I installed dovecot, and after reading tutorial after tutorial I almost got it working.

Now when I type sudo /etc/init.d/dovecot start it returns the following:
> 
Error: Can't use mail executable /usr/lib/dovecot/imap: No such file or directory [FAIL]
Fatal: Invalid Configuration in /etc/dovecot/dovecot.conf


The two are related I'm pretty sure. It didn't help at all that dovecot did *not* install the example config for me to look at. 
I also typed into terminal:
> 
locate imap_login

and it came back empty. I read on the dovecot.org site that it is supposed to install that file.. am I using the locate tool wrong or is this installation fubar?

All I want to do is use this program to enable IMAP so I can get my squirrelmail working, so far I've been thrown through so many hoops that I'm open to suggestions for another IMAP program if this can't be resolved easily.

TIA,
-SimbaSpirit
(First Post)

---

### Post by SimbaSpirit on 2008-02-22
Does anybody have any ideas? I'm totally stuck here.

---

