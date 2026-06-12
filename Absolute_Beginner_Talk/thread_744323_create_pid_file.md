---
title: "create pid file"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by BillGod on 2008-04-03
I need to run an executable file and be able to know its pid.  I am not sure how to do this.  I know ps -ef|grep name.  that will not work for me.  What I need to do is launch a process via a script file then be able to kill the process later by another script file.  If anyone can point me in the right direction it would be appreciated.

Thanks

---

### Post by finer recliner on 2008-04-03
```

davef@laptop:~$ emacs &         #run emacs in the background
[1] 17458
davef@laptop:~$ pid=$!             #save PID of last run process to a varialbe called $pid. **this is the command you want!**
davef@laptop:~$ ps                   #show running processes
  PID TTY          TIME CMD
16982 pts/0    00:00:00 bash
17458 pts/0    00:00:00 emacs
17484 pts/0    00:00:00 ps
davef@laptop:~$ kill $pid          #kill the process in variable $pid
davef@laptop:~$ ps                  #show processes again. (emacs was killed, as expected)
  PID TTY          TIME CMD
16982 pts/0    00:00:00 bash
17494 pts/0    00:00:00 ps
[1]+  Terminated              emacs
davef@laptop:~$ 

```

enjoy!

---

### Post by jordanmthomas on 2008-04-03
There's also pidof
For example, if I have a script called parse.py running and I want to kill it using its pid instead of killall parse.py
```
pidof parse.py
```
will return its pid

---

### Post by BillGod on 2008-04-03
setting a variable would work perfect for what I need.  But it does not seem to be working for me.

root@billtest-1:~# balance mysql 10.10.2.199 10.10.2.200
root@billtest-1:~# pid=$!
root@billtest-1:~# ps -ef|grep balance
root      4938     1  0 15:43 pts/0    00:00:00 balance mysql 10.10.2.199 10.10.2.200
root      4940  4908  0 15:43 pts/0    00:00:00 grep balance
root@billtest-1:~# kill $pid
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
root@billtest-1:~# echo "$pid"

root@billtest-1:~#

does not look like its getting set.

---

### Post by bovus on 2008-04-03
try:
% set pid=$!

---

