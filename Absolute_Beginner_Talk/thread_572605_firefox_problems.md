---
title: "firefox problems"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by InsertNameHere on 2007-10-10
When I start it it says theres already a firefox running but not respondin.... please close ...

Then when i went in the command i typed in

killall firefox

didn't seem to work.

I was playing with auto save sessions so Im not sure if that has anything to do with it, but it would also be great if someone tell me how to delete saved sessions

(im in feisty and I cant see default when I go in sessions)

---

### Post by twiceasworn on 2007-10-10
I would just do a:
```

ps axww |grep firefox
```

Find the PID of the already running browser then do a: 
```

kill -9 *pidnumber*
```

---

### Post by milosz.galazka on 2007-10-10
there is better (then killall) command for sending signals by proces name:
pkill -9 firefox

---

### Post by InsertNameHere on 2007-10-10
Thanks it works now =D

---

