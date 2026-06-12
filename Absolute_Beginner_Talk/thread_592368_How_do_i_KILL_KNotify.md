---
title: "How do i KILL KNotify????"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by mosquitonl on 2007-10-26
hi,

i'm running KMess on Ubuntu 7.10. since the version of KMess is buggy and no newer version is availible yet, i have to cope with not being able to turn off KNotify. at first this was do-able, but it's starting to become a pain in the *ss now. i'm now in a mood for killing. how do i KILL this annoying program and send it to hell forever???

thanks a LOT! :)
mosquitonl

---

### Post by reza81 on 2007-10-26
type xkill in the termininal. Than click on the program you want to kill!

*At your own risk*

---

### Post by Nachtengel on 2007-10-26
Also if you're running on the command line use
```
ps aux | grep KNotify
```
 note the 2nd number (which is the process ID number) and then 
```
sudo kill -9 *pid*
```
where *pid* is replaced with the process ID number noted from the first step.

---

### Post by mosquitonl on 2007-10-28
okay thanks guys, but what i meant is to make it not come back :lolflag: it seems it keeps resetting itself

---

### Post by Rinzwind on 2007-10-28
> **Nachtengel said:**
> Also if you're running on the command line use
```
ps aux | grep KNotify
```
 note the 2nd number (which is the process ID number) and then 
```
sudo kill -9 *pid*
```
where *pid* is replaced with the process ID number noted from the first step.

Too much work for me :+
```

sudo killall KNotify 

```

is easier.

Use at own risk :)

---

