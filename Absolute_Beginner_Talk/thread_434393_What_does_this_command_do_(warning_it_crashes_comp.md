---
title: "What does this command do? (warning it crashes computer)"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by davidY on 2007-05-05
Hello, i just found the following bash code that will completely kill your computer. I AM NOT LYING  - UNDER NO CONDITION RUN THIS CODE. But anyway, how does and what does this bash ocde do?

```
(:(){ :|:;};:)
```

---

### Post by roachk71 on 2007-05-05
This is a particularly diabolical piece of self-replicating code (also called a fork bomb).
In this case, the same function is recursively forked twice (per recursion), and this rapidly fills up the process table, causing a denial-of-service condition.

Frankly, I'm kinda shocked that modern shells don't catch and disallow this kind of logic bomb...

---

### Post by big_area on 2007-05-05
looks kinda like a "malloc monster" a friend of mine wrote a few yrs back.
basically it allocated memory until the thing crashed.... i think it was written in c tho


i.e. i have no clue but as the doctor says: "if it hurts, dont do it"

---

### Post by big_area on 2007-05-05
ah close.....



:guitar:

---

### Post by Schalken on 2007-05-05
Does it work when run as a user? If so, then this is a security issue.

---

### Post by davidY on 2007-05-05
```
found on a forum: Hal Pomeranz hal at deer-run.com

It creates a function called ":" that accepts no arguments-- that's
the ":(){ ... }" part of the utterance.

The code in the function calls the recursively calls the function
and pipes the output to another invocation of the function-- that's
the ":|:" part.  The "&" puts the call into the background-- that way
the child process don't die if the parent exits or is killed.  Note
that by invoking the function twice, you get exponential growth in
the number of processes (nasty!).

The trailing ";" after the curly brace finishes the function definition
and the last ":" is the first invocation of the function that sets off
the bomb.

Most unpleasant...
```

---

### Post by noerrorsfound on 2007-05-05
> **roachk71 said:**
> This is a particularly diabolical piece of self-replicating code (also called a fork bomb).
In this case, the same function is recursively forked twice (per recursion), and this rapidly fills up the process table, causing a denial-of-service condition.

Frankly, I'm kinda shocked that modern shells don't catch and disallow this kind of logic bomb...
More information for the curious: [http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb) :)

---

