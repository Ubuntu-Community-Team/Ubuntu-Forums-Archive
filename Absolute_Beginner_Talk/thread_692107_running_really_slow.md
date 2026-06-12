---
title: "running really slow?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2008-02-09
i have ubuntu dapper, running on a dell inspiron notebook that is about a year and a half old.  every now and then, my computer starts running *really* slow, regular apps take forever to open and load, and admin apps wont even come up. do you think this is an ubuntu problem or just that my computer is getting old? ive tried reinstalling ubuntu when it gets really bad and it seems to help for a little while, but it usually ends up happening again.

it almost makes me miss windows, and thats something i thought id never say. :-p

---

### Post by taurus on 2008-02-09
How much RAM does it have and what is the size of the swap partition?

```
free
```

---

### Post by irishgoth8822 on 2008-02-09
total       used       free     shared    buffers     cached
Mem:       1026836     464324     562512          0       8196     189180
-/+ buffers/cache:     266948     759888
Swap:      3004112          0    3004112

---

### Post by jan quark on 2008-02-09
it seems there is enough free memory to me

perhaps a process is taking away the speed

you can run the command
```

top
```

to view the current processes

anything unusual there?

---

