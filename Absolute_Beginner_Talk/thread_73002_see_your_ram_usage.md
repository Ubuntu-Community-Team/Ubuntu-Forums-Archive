---
title: "see your ram usage?"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by sunrex on 2005-10-07
im currently running a Counter Strike Source server on SERVER ONLY install.

how do i check my current ram usage? i need to know this lol..

no im not a noob. i just think this was the best place to post this stuiped question lol.

thanks, 

darksoul

---

### Post by Wide on 2005-10-07
Is, "top" in the command line what your looking for?(without the " "):D

---

### Post by ow50 on 2005-10-07
To display only the memory usage, use command "free".

---

### Post by SilentCacophony on 2005-10-07
Also, keep in mind that linux dynamically uses free memory for buffers, so the actual usage without buffers is on the second line:

```
brian@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        451680     366168      85512          0      28148     203220
-/+ buffers/cache:     134800     316880 <- here
Swap:      1020088          0    1020088
```

---

