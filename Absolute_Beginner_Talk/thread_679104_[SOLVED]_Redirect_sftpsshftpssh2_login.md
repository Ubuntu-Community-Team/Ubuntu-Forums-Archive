---
title: "[SOLVED] Redirect sftp/ssh/ftp/ssh2 login"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2008-01-26
Hey all

I'm running a server, and most users prefer to login using sftp rather than ssh through a terminal.  I was able to redirect for an ssh login just by editing the .profile (adding cd /media/Backup) at the end of it.

However, when someone goes thru sftp, they are logged into /home/guest... i want them to be logged into /media/Backup

anyway to change this besides changing 'guest's' home directory to /media/Backup?

Thanks,
kt

---

### Post by sisco311 on 2008-01-26
you can create a symbolic link:
```
sudo ln -s -T /media/Backup/ /home/guest
```

remove first the /home/guest dir

---

### Post by kernel tom on 2008-01-26
i want guest to have  /home/guest

but i want guest to be redirected to /media/Backup upon login

---

### Post by kernel tom on 2008-01-28
anyone?

---

### Post by kernel tom on 2008-01-28
I really need help with this...

the only way i've been able to do this is by...

sudo usermod -d /media/Backup/ guest

there has to be another option

---

