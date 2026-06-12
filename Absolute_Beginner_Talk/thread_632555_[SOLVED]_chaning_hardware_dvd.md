---
title: "[SOLVED] chaning hardware dvd"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-12-05
I have a dvd player that has never worked. Well it worked before Ubuntu, but I don't speak to Mr. Gates anylonger.

I want to swap the dvd player I have for another that (although used) probably works. It's also a dvd r-w. 

Once it is physically installed on the cable, with the jumper set properly, what do i need to do to have Gutsy "recognize" it?

---

### Post by jasmuz on 2007-12-05
You dont have to do anything for it to be recognized, recognition is done by the Kernel itself when it boots up.

I do recommend that after boot up, you check your system logs to see if it placed it in the same channel as the previous one, if it did.. there wont be any issue at all.

---

### Post by Mark_in_Hollywood on 2007-12-05
> **jasmuz said:**
> You dont have to do anything for it to be recognized, recognition is done by the Kernel itself when it boots up.

I do recommend that after boot up, you check your system logs to see if it placed it in the same channel as the previous one, if it did.. there wont be any issue at all.

So where is this channel? And what should "check?"

---

### Post by jasmuz on 2007-12-05
I meant the IDE channel and Master-Slave configuration as before.

The logs are everywhere... but there is a nice log reader, in:
Menu-->System-->System Log

---

