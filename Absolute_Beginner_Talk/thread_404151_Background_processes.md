---
title: "Background processes"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by guitarra1809 on 2007-04-08
Hello there.
For some reason, I am not able to run processes in the bacground.
Namely, everytime I run a command in the background, for example  pico & , the job will be in the [Stopped] state.
Applying bg %JobNumber won't do, and the only way to resume the process seems to be "fg".

Is this a known issue with UBUNUTU? Is there anyway to overcome it? I'd hate to think I can't work with processes in the background...

---

### Post by mlissner on 2007-04-08
This isn't a problem I've ever heard of, and I run Ubuntu, so it's not an issue with Ubuntu specifically. 

Quite a strange issue - Let's try some troubleshooting. What do you get when you do a ps? Does it say you are running bash or dash? I've heard that some versions of Ubuntu run dash, which could be different in this regard (I don't know for sure, but it's a thought). If that's the case, try opening up a terminal and running bash and see if the same problem happens there.

Another thought is just to open up, say, csh and see if it happens when you do that. Might isolate the problem a bit.

---

### Post by guitarra1809 on 2007-04-08
I have bash installed.
I do not have csh.
The same problem occures in sh too.
It is strange indeed...

---

