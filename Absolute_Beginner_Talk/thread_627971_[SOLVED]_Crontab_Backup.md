---
title: "[SOLVED] Crontab Backup"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-30
Hello.... a simple one I am sure...what is the crontab command to backup all of the sub-directories & files in a backup directory to a usb key.

The following only backs up the[COLOR="Red"] files[/COLOR] in the directory.....no sub-directories!

* * * * * rsync ~/Documents/Backup/*.* /media/disk/

Thanks


Bern

---

### Post by Dr Small on 2007-11-30
Try adding the "-r" argument to rsync, for Recursive.
Also, try man rsync for the manual.

---

### Post by bern1939 on 2007-11-30
Thank you very much.

Bern

---

### Post by Dr Small on 2007-11-30
No Problem, if it helps, please mark this thread as Solved from Thread Tools :)

---

