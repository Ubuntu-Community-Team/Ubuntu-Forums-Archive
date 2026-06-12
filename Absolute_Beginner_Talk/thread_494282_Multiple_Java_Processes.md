---
title: "Multiple Java Processes"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Stupojohn on 2007-07-06
Somehow, while trying to install Java, I managed to install it several times (at least that's my self-diagnosis).  
After installing I noticed that my computer seemed a bit slow.  I checked my System Monitor, and it shows the process "jre-6u2-linux-i" running 4 times, each using about 20% CPU.  How can I get rid of at least three of these?

On an unrelated note, should Xorg always be using about 7% CPU?  Thanks in advance!

---

### Post by DSn0wMan on 2007-07-06
To kill the java processes you can do the following in the terminal.

```
ps -ef | grep jre-6u2-linux-i
```

This will give you the process id in the first column then just kill the process ID for example if the process ID is 6648 the issue the following command

```
kill 6648
```

If that doesn't kill it then do a kill -9 instead.

---

