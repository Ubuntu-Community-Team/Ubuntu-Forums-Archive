---
title: "Need a command"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by crypticstatic on 2006-08-07
I have a HDD with several partitions on it and most of the disk space is being used up on / 

I have a different partition for for /usr, /log, /etc /home and /var

What is the best command or command syntax to use to find out exactly what is chewing up so much disk space on / ?

Thanks in advance!

---

### Post by kaamos on 2006-08-07
You can install a graphical tool called baobab (use synaptic), or use the command
```
cd /
sudo du -h --max-depth=1

```
You can then change directories and the max-depth parameter for more specific results. Try also sudo du --max-depth=1 | sort -gr

Hope this helps.

---

### Post by crypticstatic on 2006-08-07
Worked great! Thats what I was looking for. Thanks!

Cryptic

---

