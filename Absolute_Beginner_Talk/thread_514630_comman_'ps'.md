---
title: "comman 'ps'"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Rudy507 on 2007-07-31
hey guys,
I'm not a REAL newbie, but this is a newbie question...

Anyway, I just installed the program frozen-bubble (it's a game) via the command apt-get install yadda yadda yadda

Anyway, it's running, and now I want to close it. Like an intelligent human being, I take my mouse over the x and try to close it, but it doesn't close. So I go into the prompt and type 'ps' in order to get the ID and then manually kill it ... and the only two processes it displays is bash and ps!

So I try ps -a

Still nothing.

So I try one more thing: sudo ps -a

Still nothing.

So, uhh... any suggestions?

Thanks,
David

---

### Post by Inxsible on 2007-07-31
try to do a ```
top
``` in the terminal to see if it will give you a PID. Use that PID to kill it

```
kill PID
```

---

### Post by splintercellguy on 2007-08-01
ps -A?

---

### Post by meierfra on 2007-08-01
sudo pkill  frozen-bubble

---

### Post by Paul133 on 2007-08-01
It's ```
ps -A
``` not ```
ps -a
```.

---

### Post by DirtDawg on 2007-08-01
Also, you can right-click your top or bottom panel and go to the "Add To Panel" option and add "Force Quit." This creates a nice Force Quit button you can use any time.

Force Quit is my friend. And it's your friend too.

---

### Post by tomcheng76 on 2007-08-01
ps aux |grep frozen-bubble
kill -9 <process ID of frozen-bubble>

---

### Post by mcduck on 2007-08-01
Just select 'Exit' from Frozen Bubble's menu :D

---

