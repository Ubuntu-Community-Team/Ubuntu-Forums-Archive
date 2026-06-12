---
title: "how do i refer to another drive?"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Mick8882003 on 2008-03-27
I want to dump a backup to another drive

eg
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

i want to change to backup to the "michael carey" drive.

---

### Post by mikewhatever on 2008-03-27
> **Mick8882003 said:**
> I want to dump a backup to another drive

eg
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

i want to change to backup to the "michael carey" drive.

Where is it mounted? Post the output of <df>.

---

### Post by Mick8882003 on 2008-03-27
mickpc@mickpc-desktop:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sdb1            234402784  22204016 200291796  10% /
varrun                 1033520        92   1033428   1% /var/run
varlock                1033520         0   1033520   0% /var/lock
udev                   1033520        76   1033444   1% /dev
devshm                 1033520         0   1033520   0% /dev/shm
lrm                    1033520     34696    998824   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             97900076  14934396  82965680  16% /media/Michael Carey
mickpc@mickpc-desktop:~$

---

### Post by Trail on 2008-03-27
tar cvpzf /media/example/folder/backup.tgz ...

Normally your partition would be located on /media. You can right-click on the drive's icon on the desktop, hit properties, and see which one it is.

Edit: Too late:
```

tar cvpzf /media/Michael\ Carey/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

```

Notice the backslash after Michael to escape the space character.

---

