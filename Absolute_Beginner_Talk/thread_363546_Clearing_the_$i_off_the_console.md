---
title: "Clearing the $i off the console"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-02-17
When I use a code in console that involves $i or some other thing (what is the $i thing called?), it would stay coded.  How do I clear it?

You know when you do a:
```
i=foo; echo $i
```
And then echo again and again, the $i would stay coded.  I know it can be replaced, but I would like to know how to clear it.

---

### Post by highneko on 2007-02-17
i="" maybe?
highneko@ubuntu:~$ i=""; echo "a${i}a"
aa
highneko@ubuntu:~$

If there's a command then I don't know it.

---

### Post by petit.padavoine on 2007-02-17
$i is called a variable (system variable in that case).
This variable is only still "coded" for your current session. If you open a new Terminal or tab, the variable won't be there anymore :D.

---

