---
title: "cvs password?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by falkenberg_cph on 2006-06-16
hi
Whats a cvs password, and do i have one?

Carsten

[EDIT:] Heres is some of my problem from the terminal:
Logging in to :pserver:anonymous@hostap.epitest.fi:2401/cvs
CVS password:
cvs login: CVS password file /home/name/.cvspass does not exist - creating a new file

---

### Post by loell on 2006-06-16
you should acquire one, if that particular cvs source requires you so..
however most of the opensource cvs such as in sourceforge does allow anonymous cvs check out, and does not require a password...

---

### Post by falkenberg_cph on 2006-06-16
This cvs does seem to need a password. Its a partuclar problem for this How-To:

[http://www.ubuntuforums.org/showthread.php?t=125150&highlight=keyring](http://www.ubuntuforums.org/showthread.php?t=125150&highlight=keyring)

how do i aquire a pass.

Carsten

---

### Post by loell on 2006-06-16
this cvs doesn't require you a password..

i've checkout for this cvs succesfully

cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs login
cvs -d :pserver:anonymous@hostap.epitest.fi:/cvs co hostap

if password prompts, just hit enter key

---

### Post by falkenberg_cph on 2006-06-16
Thats weird. I tried it several times before. But you&#341;e right.
Thanks anyway, now i know for the future

---

