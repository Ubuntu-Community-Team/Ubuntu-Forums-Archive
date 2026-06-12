---
title: "Slow Ubuntu problem"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by T2manner on 2008-03-22
Something is wrong.
it's going rather slow.

i'm not sure what the problem is.
it's MAINLY firefox 2 that is slow.

however firefox 3 isn't.

but is there anything that could be slowing my ubuntu down?

---

### Post by jan quark on 2008-03-22
you can run

```
top
```

in terminal to view the processes which are running
anything unusual ?

---

### Post by T2manner on 2008-03-22
i'll try that when i get back on ubuntu
i'm on XP running a virus scan bcs it is being unusually slow too.

---

### Post by T2manner on 2008-03-22
okay i went to terminal and did some stuff:

tyler@Tyler:~$ free -t
             total       used       free     shared    buffers     cached
Mem:       1034608     679988     354620          0      14308     333268
-/+ buffers/cache:     332412     702196
Swap:      1253028          0    1253028
Total:     2287636     679988    1607648
tyler@Tyler:~$ top

top - 15:39:08 up  1:01,  2 users,  load average: 0.40, 0.52, 0.32
Tasks: 103 total,   3 running, 100 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.3%us,  4.7%sy,  0.0%ni, 88.0%id,  0.0%wa,  0.7%hi,  0.3%si,  0.0%st
Mem:   1034608k total,   694192k used,   340416k free,    14540k buffers
Swap:  1253028k total,        0k used,  1253028k free,   344968k cached


is any of this bad

---

### Post by T2manner on 2008-03-22
bump it up

---

### Post by MadMedis on 2008-03-22
That looks pretty similar to the results I get when I run top, so it doesn't look too bad to me at first glance.  Are there any running processes that you don't recognize?  

Also, is everything slow or is it just a few applications?  You mentioned that Firefox was slow and that your windows XP installation was also slow; is there a chance that your network is slow?

---

### Post by T2manner on 2008-03-22
it seems to be working now.
both times it was slow i was trying to play a java game on pogo.com
on ubuntu it just froze up, but windows it just went VERY slow
i think that was it 
not sure though

---

