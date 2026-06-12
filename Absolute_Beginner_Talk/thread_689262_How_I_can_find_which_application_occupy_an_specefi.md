---
title: "How I can find which application occupy an specefic port?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-02-06
Hi
Thank you for reading my post
Is there any way to find the process that occupy an specific port?
I know that 3888 port is occupied by a process because its shows when i execute
```

netstat -an |grep EST

```

but I can not find the application that occupied this port, I want to kill that process.
or close the connection because i need that port for other purposes.


Thanks

---

### Post by Trail on 2008-02-06
man netstat:
```

   -p, --program
       Show the PID and name of the program to which each socket belongs.

```

---

### Post by jan quark on 2008-02-06
try

```
sudo lsof -i
```

and for more info

```
man netstat
```
```
man lsof
```

---

