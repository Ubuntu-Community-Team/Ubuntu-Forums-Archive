---
title: "Can't kill cupsd"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-03-07
So I don't know what happend but cupsd is now consuming 100% of one of my two cores!
I can't kill it.

I tried
sudo killall cupsd
sudo killall ProcessID

I tried restarting, 
I even pulled the plug out of my machine and it restarts with cupsd going crazy!

how can I kill this process?

---

### Post by Daveth on 2008-03-07
I always run "top" in a terminal, find the PID number of the offending process, and kill that. Might not be the proper way be it seems to work!

---

### Post by neurostu on 2008-03-07
So I used top to find the pid, and trying:
```

sudo killall <pid>

```
did nothing

---

### Post by Daveth on 2008-03-07
kill pid number should work - I just opened and then killed OO with it by killing its PID, no sudo involved.
Do you actually know why cups in running wild? Is it a print queue thing? Just wondering if killing it will actually kill it, or will it rise, ghoul like!

---

### Post by neurostu on 2008-03-07
I'm not really sure what is going on. 

I know that kill pid should kill anything...

What really is weird is when I reboot cupsd is still there!
Even if i pull the plug without shutting down it is still there! 

I really am lost here

---

### Post by Daveth on 2008-03-07
have you poked around in cups through the web interface?

[http://localhost:631/admin](http://localhost:631/admin)

in a browser? Just a thought. Been searching other linux fora for you, but no joy yet - mostly about cupsd not running. Typical!

---

### Post by PinkFloyd102489 on 2008-03-07
Install the program htop, which is an extended top program with colors and more functions. Find the cups process, press F9, and on the left side select SIGTERM then hit Enter. This should kill off the program.

---

### Post by neurostu on 2008-03-09
bump

---

### Post by Oldsoldier2003 on 2008-03-09
> **neurostu said:**
> bump

did you try kill -9 ?

---

### Post by neurostu on 2008-03-09
what is ```
 kill -9 
```

---

### Post by Oldsoldier2003 on 2008-03-09
> **neurostu said:**
> what is ```
 kill -9 
```

```

 Name     Num   Action    Description
  KILL       9        exit         this signal may not be blocked
```

kill -9 <pid>

---

### Post by herbster on 2008-03-09
```
kill -s 9 PID
```

kills the unkillable for me.

---

### Post by neurostu on 2008-03-10
kill -9 <pid> did it!

Thanks

---

