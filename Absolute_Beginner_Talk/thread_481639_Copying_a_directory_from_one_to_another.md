---
title: "Copying a directory from one to another"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-06-22
I have a folder called 'bin' on my desktop that I'd like to move to ~/.wine/drive_c/Program Files/BYOND.

I tried cp bin ~/.wine/drive_c/Program Files/BYOND but it doesn't seem to work.  Is it possible to copy whole directories and move them to another?

```
taylor@ubuntu:~$ sudo -s
Password:
root@ubuntu:~# cd Desktop
root@ubuntu:~/Desktop# cp bin /home/taylor/.wine/drive_c/Program\ Files/BYOND
cp: omitting directory `bin'
root@ubuntu:~/Desktop# 
```

---

### Post by diatribe on 2007-06-22
cp -r

---

### Post by coffeecat on 2007-06-22
Sorry. Posted in error.

---

