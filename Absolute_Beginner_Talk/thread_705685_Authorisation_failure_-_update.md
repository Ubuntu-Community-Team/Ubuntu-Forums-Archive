---
title: "Authorisation failure - update"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by jonnieH on 2008-02-23
Posted a query on this site a little while ago concerning loss of su privileges after a failed software install. Though all was now ok as sudo now appears to work (although it didn't initially even though I am POSITIVE I used the correct password) However su still fails thus:-



john@john-desktop:~$ su
Password: 
su: Authentication failure
Sorry.
john@john-desktop:~$ 

(this is after I fixed the broken sw package)

Any ideas Please?

jonnieH

---

### Post by taurus on 2008-02-23
Which password did you use?  Did you use your login password or did you use root's password?

---

### Post by mahuyar on 2008-02-23
```
 sudo su 
``` and type in john's password.  Then change your root password, but I don't see the point since you've already gained root privileges.  As for why "su" no longer works after a failed software install, I have no idea.

---

### Post by jonnieH on 2008-02-23
Thank you all for your patience, I'm a dinosaur  who used to be a systems administrator on a unix system about 100 years ago (seems like) Too many lost brain cells to remember the strange incantations we used to use. root password now reset and hopefully all OK


JonnieH

---

