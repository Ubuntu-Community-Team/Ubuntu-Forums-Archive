---
title: "Date command"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by ramdisc on 2005-11-19
Hello,

Would someone please tell me how to use the date command?  I have RTFM, but I don't understand how to use it.

I am trying to get YYYY-MM-DD HH:MM

So I entered this **date --set=%F %R** and many other combinations, but I cannot figure it out how to the string to work.

Please help.  Thanks in advance.

---

### Post by invalid on 2005-11-19
```
date +%F' '%R
```
should work for what you require.

Cheers,
Cb

---

