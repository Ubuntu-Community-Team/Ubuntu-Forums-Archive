---
title: "HAL problem"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by richaoj on 2008-02-25
for some reason i've been having some problems dealing with hal.  For some reason this keeps popping up:

```
sudo /usr/lib/hal/open-podbay-doors
HAL:I'm sorry Dave, I'm afraid I can't do that. 
```

Can someone please help me with this problem.  I'm trying to shut HAL down, but for some reason I can't.

---

### Post by gimfred on 2008-02-25
I'm not sure if this is a joke or not... That is the reference to the book/movie Space Odyssey 2001... 99% of me thinks this is a troll... But in the interest of good will, I shall answer this.

To stop hal (Are you sure you need to do this?) the daemon you are looking is hald. Please type at the command line (CLI):
```
man hald
```

The command you are looking for is:

```
/etc/init.d/haldaemon stop
```
and apparently you should then run 
```
pkill hald
```

to start it again is really simple (in case you haven't guessed):
```
/etc/init.d/haldaemon start
```

Please don't just do these things randomly, they may cause system instabilities...

---

### Post by richaoj on 2008-02-25
I wasn't trying to troll, but this came to me and I thought it was funny.  
open-podbay-doors!?  

nevermind

---

