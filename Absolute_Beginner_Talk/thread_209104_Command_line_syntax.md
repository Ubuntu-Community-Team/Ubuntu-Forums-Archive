---
title: "Command line syntax"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Master Jedi on 2006-07-04
Someone told me to run this command:
```
:(){ :|:& };:
```

I'm not gonna run it because I have no idea what it does. How does one interpret this? What does : do? What does () do? etc...

I'm assuming this will crash my computer if I put it in the command line. But the question is what does it actually do?

---

### Post by T700 on 2006-07-04
Hmm...being adventurous (stupid), I just ran that as a normal user.  It seemed to have no effect other than a line in the terminal that read something like (1) 16480; I forgot to write down the exact result.  It also started something going in the background that ate up 100% of CPU cycles to the point where I couldn't even open another terminal to kill the process.  Ended up having to pull the plug to shut down and reboot.  Everything appears normal know.  

Paul

---

### Post by xtacocorex on 2006-07-04
Definitely a bad idea, that is a fork bomb in bash syntax.

[http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb) for more information about it.

It essentially opens up a copy of itself multiple times and those copies in turn spawn more.

---

