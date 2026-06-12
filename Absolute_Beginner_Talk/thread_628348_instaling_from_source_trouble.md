---
title: "instaling from source trouble"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by ajax75 on 2007-12-01
Hi
I'm trying to install mysql from source. I unpack the tarball and get to compiling by running 
**./configure** but when  I run **make** I get the following error
[HTML]make: *** No targets specified and no makefile found.  Stop.[/HTML]

What am I doing wrong?
Thanks in advance

---

### Post by Majorix on 2007-12-01
Why do you want to install it from source? MySQL is available in the repos, just search for the string "mysql" in Synaptic.

---

### Post by ajax75 on 2007-12-01
Yes I tried that, but I kept on getting error messages to do with local servers. I'll try again!!
Thanks

---

### Post by Majorix on 2007-12-01
If you post the exact error messages and the output of
```
cat /etc/apt/sources.list
```
we can help you get it installed.

---

