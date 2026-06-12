---
title: "Why doesn't this work?"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-02-27
I'm trying to set clamscan to scan my /home dir every day at 5 am, and report any problems via email to me@localhost

i.e.

crontab * 5 * * * clamscan -r -i /home |sendmail -t me@localhost

It returns;
crontab: invalid option -- i
crontab: usage error: unrecognized option
usage:  crontab [-u user] file
        crontab [-u user] { -e | -l | -r }
                (default operation is replace, per 1003.2)
        -e      (edit user's crontab)
        -l      (list user's crontab)
        -r      (delete user's crontab)

But according to the crontab wiki this should work. What am I doing wrong please.

The funny thing is, if I do crontab -e and manually edit the file, it works!!

---

### Post by ubuntuuser on 2006-02-27
I am just guessing, but have you tried to use quotes?```
crontab * 5 * * * "clamscan -r -i /home |sendmail -t me@localhost"
```

---

### Post by LordBug on 2006-02-27
As Ubuntuusuer mentioned, try with quotes:

crontab * 5 * * * "clamscan -r -i /home |sendmail -t me@localhost"

Crontab will then see everything between them as one big input, instead of multiple options for itself.

---

### Post by My-dial-up on 2006-02-27
Had to use the ` quote character - the one above the TAB key.

But thanks for the pointer.

---

