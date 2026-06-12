---
title: "[SOLVED] How do i increase open files (-n) 1024 limit??"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-12-12
Hi,

I'm using aMule and i always get error "too many open files"

I tried:
editing the file /etc/security/limits.conf
firebox soft nofile 1024
firebox hard nofile 65535

with no luck... e.g.
firebox@firebox-desktop:~$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 6140
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
[COLOR="Red"]open files                      (-n) 1024[/COLOR]
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 6140
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

what can i do??

thanks..

---

### Post by hopelessone on 2007-12-12
Fix:

edit /etc/security/limits.conf

and add :
[username] soft nofile 4096
[username] hard nofile 4096

hope that helps others...

cheers...

happy aMuling...

---

### Post by strutzz on 2008-01-03
i ussed the comand in terminal, but i had an error, I accesd the file using nautilus with "sudo nautilus" and added the line(with username= my logon name and worked fine . Thks > **hopelessone said:**
> Fix:

edit /etc/security/limits.conf

and add :
[username] soft nofile 4096
[username] hard nofile 4096

.

---

### Post by pocketchange on 2008-06-13
I ran into the same problem.  Just for clarity, you'll have to logout and log back in before these will take effect.

---

