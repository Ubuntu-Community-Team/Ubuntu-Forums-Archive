---
title: "nothing opening up at all. Ugent!"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by guiltymilkshake on 2007-10-23
no programs are opening for me. there was an error with open office and I closed it. no no programs are opening up. they act like they are and it says they are loading but then nothing happens. anything I can do?

---

### Post by rudeboyskunk on 2007-10-23
If possible, go to System Monitor (or something like that, sorry, I'm at work on a Windows computer).  There's probably a program eating up all your resources.  Right click on it and click "Kill Process."

---

### Post by guiltymilkshake on 2007-10-23
thanks for the response. I tried opening up system moniter and it did the same. I am not even exiting out of firefox cause I know it wont open.

---

### Post by guiltymilkshake on 2007-10-23
also, i know i can restart and fix it but i am in class right now and if i restart it will make noise :(

---

### Post by Shiva88 on 2007-10-23
Can you get a terminal?

---

### Post by guiltymilkshake on 2007-10-23
no i cant. it just says "opening terminal" and then just dissapears off the task bar. it does this for every program.

---

### Post by Dr Small on 2007-10-23
> **guiltymilkshake said:**
> also, i know i can restart and fix it but i am in class right now and if i restart it will make noise :(
Unplug the speakers...
But anyhow, you can access a virtual terminal by pressing CTRL + ALT + F1.

Then you can run:
```
ps aux | grep office
```

Find the pid number of open office (or the offending application), and then type:
```
kill *pidnumber*
```

Then switch back to X with ALT + F7

Dr Small

---

