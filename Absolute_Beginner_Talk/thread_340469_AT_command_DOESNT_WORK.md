---
title: "AT command DOESNT WORK"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by 09adi09 on 2007-01-17
Hey I want to schedule a job with at as
at <some_time>
> mplayer <some file>
> Clrl+D

The job just doesnt excute at the given time.The /etc/at.allow file doesnt exist and the /etc/at.deny file is empty.
(It had some processes and daemons in it..I deleted them).
Any help would be brilliant...

---

### Post by ice60 on 2007-01-17
hi you might need to startup the at daemon. i'm not using ubuntu, but i think this will start it 
```
/etc/init.d/atd start
```

actually you can run this to see if it's running first
```
/etc/init.d/atd status
```

---

### Post by ice60 on 2007-01-17
i have these notes about using the at command if you want them??

to list scheduled jobs ```
at -l
```

to remove one of the listed jobs (should have a number)
```
atrm (number)
```

---

### Post by 09adi09 on 2007-01-17
I checked for the running of the atd daemon with
ps -e | grep atd
and it was running....

I still am not able to have the "at" command work though ](*,)

---

