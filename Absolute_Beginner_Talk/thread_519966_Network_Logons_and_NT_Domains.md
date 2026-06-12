---
title: "Network Logons and NT Domains"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by wjhildreth on 2007-08-07
Hello all,

   Please forgive me if this has been asked before.

1) How can ubuntu use a network logon like Windows does with a Domain controller?

2) Is it possible to have network logons fron both ubuntu and Windows to a Linux server?

3) What tools or software needs to be setup to make this sort of stuff work.

4) Does SAMBA have to be used to make both platforms work together?

5) What is used in an all Linux environment for network authentication?

6) What reading resources can you point me to to learn what I need to know?

   Many thanks for your time and energy to this newbie trying to move from Windows to Linux.

Warm Regards,

Joe Hildreth

---

### Post by wirelessmonkey on 2007-08-07
A few short answers for you, I'm not up to date on the details, but I'll be thinking about it for certain.

1) Creating a Samba DC
2) Yes
3) Samba and a DC (win or lin)
4) Yes, in general, though they can interact with ssh/sftp/ftp/rsync/etc.  But those are all limited.
5) We use kerberos/ldap with SAMBA domain controllers containing user credentials.  I'm sure there are many other methods.
6) urp... I'll see what I can find.

---

### Post by wjhildreth on 2007-08-14
Thanks for the info. Do you have any links to some resources that a newbie can follow and learn for some of this stuff?

Regards,

Joe

---

