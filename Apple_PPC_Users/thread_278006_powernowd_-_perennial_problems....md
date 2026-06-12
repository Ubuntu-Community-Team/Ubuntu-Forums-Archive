---
title: "powernowd - perennial problems..."
date: 2006-10-15
forum: Apple PPC Users
---

### Post by pauljwells on 2006-10-15
I have a 12" 1GHz AlPB running Dapper and OSX10.4

I have never been able to get cpu frequency scaling to work without panicking the kernel either with OSX or Ubuntu. I found that in OSX I have to set the cpu frquency to be a fixed value, in Ubuntu I had to disable powernowd.

Doing this resulted in changing a system that would hang after 15 minutes to one that was rock solid in either OS.

UNTIL NOW!! with Dapper in its current state, powernowd works beautifully and my cpu runs 5 - 10 degrees C cooler as a result.

I just tried the Edgy live CD, and this hangs when the cpu frequency changes, so looks lke powenowd is broken again.

Am I the only person who has such an issue with powernowd??

---

### Post by pauljwells on 2006-10-30
I just upgraded my Powerbook to Edgy and decided to bump this thread.

Powernowd is once again killing my system

Does no-one else have this problem but me????

---

### Post by dgtester on 2006-12-01
I have the same problem on my dell inspiron (random freezes after a few minutes, usually while doing something processor intensive). I just downgraded to the dapper version of powernowd and everything's fine.

---

