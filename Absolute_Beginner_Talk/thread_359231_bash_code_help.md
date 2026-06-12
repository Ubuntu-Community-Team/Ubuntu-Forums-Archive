---
title: "bash code help"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-02-11
If I tried to ping www.zubuntu.com, I would get a "unknown host" sent back to me.

But this code would not work properly:
```

if ping -c 1 www.zubuntu.com | grep -q "unknown host"; then echo "ping failed"; else echo "got ping"; fi

```
Because the response I got back is not included.

How do I make the code to include the response sent back to me from ping?

Note that this is not about the ping, it is about the code responding properly to something sent back to it.

---

### Post by machoo02 on 2007-02-11
do you mean **x**ubuntu?

---

### Post by raptros-v76 on 2007-02-11
it has to do with the difference between stdout and stderr i think. 
i think ping, when saying unknown host, is sending it to stderr, while grep is looking for something on stdout. the advance bash scripting guide (abs-guide in the repos) has stuff about redirection that you may find useful. good luck!

---

