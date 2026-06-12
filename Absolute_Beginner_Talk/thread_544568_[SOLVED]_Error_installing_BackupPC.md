---
title: "[SOLVED] Error installing BackupPC"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-06
Hi,

I installed backuppc using

```
sudo apt-get install backuppc
```but I get this error:

```
 * Starting backuppc...
Can't create LOG file /var/lib/backuppc/log/LOG at /usr/share/backuppc/bin/BackupPC line 1735.
```

There are no other errors. Any ideas to fix? I'm using Ubuntu Server 7.04.

Thanks.

---

### Post by lee_connell on 2007-09-06
Looks like a permission issue on /var/lib/backuppc/log/LOG 

sudo chown backuppc -R /usr/share/backuppc
sudo chown backuppc -R /var/lib/backuppc

then sudo dpkg-reconfigure backuppc or sudo aptitude reinstall backuppc

---

### Post by alishad on 2008-03-18
I was having the same problem and reinstalled the package.  I am still receiving the same error message.  Any ideas what to do now?

---

### Post by lee_connell on 2008-03-20
Did you change permissions like i mentioned above?

---

