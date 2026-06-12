---
title: "Questions relative to the log files"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by thelugnut on 2007-11-19
I have in my "file system" 21 "xxx.log" files.

Some of these files have 0 bytes, while the largest has 407 KB.

There is one file named "term.log" which will not allow me to open.

Do these logs continue to grow forever, or am I supposed to periodically flush them clean?

Are there any files that should be left untouched?

Is there a simple way (perhaps a script) that I could run, say once a week, to do the job for me?

Thanks

---

### Post by kpkeerthi on 2007-11-19
The answer lies in 
```

man logrotate

```

and in /etc/logrotate.conf

---

### Post by thelugnut on 2007-11-19
Yes, that would be it.:)

Thanks

---

