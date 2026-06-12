---
title: "Tarbomb?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by money2themax on 2008-01-04
ok i've been reading some of your sigs and the code of conduct and i'd like to learn more about the following:

1. Tarbombs
2. forced removal of file systems
3. RAW rewrites
4. fork?
5. disk formats

---

### Post by rubicon on 2008-01-04
Um. It's strange that noone has answered yet :)

I'm not a pro, but I can begin some explanations. All that is bad things can happen to a newbie user by accident.

1. Let us imagine a file. Just plain text 'aaaaaa'. It could be compressed very much, right? Then imagine 10GiB file filled with 'aaaa'. Does it make sense? Maybe, The only reason to do such file is: tarbomb. You tar+gzip it and archive will be <10KiB in size. Pretty little bomb. Untar it and this baby will fill MUCH space.

4. Fork is like cloning, If process make fork(); it duplicates itself and continues execution from the next line after fork(); Nothing suspicious, eh? I think you already seen this: ```
:() { :|:& };: 
``` It is forkbomb, it forks and forks and forks... Until fill up all your system (OR hard-limited set of resources).

---

### Post by LaRoza on 2008-01-04
> **money2themax said:**
> ok i've been reading some of your sigs and the code of conduct and i'd like to learn more about the following:

1. Tarbombs
2. forced removal of file systems
3. RAW rewrites
4. fork?
5. disk formats

Use Wikipedia.

---

### Post by rubicon on 2008-01-04
Haven't I told you not to test it on your machine? No? **_Don't test it!_** Rather look here: [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)

---

### Post by money2themax on 2008-01-04
> **rubicon said:**
> Haven't I told you not to test it on your machine? No? **_Don't test it!_** Rather look here: [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)

no no no i haven't run them i just curious as to how they work and what they do.
you  see i'm trying to learn how to maintain a server and worstation and i wish to know how these strange yest damaging things work

---

### Post by money2themax on 2008-01-21
don't worry but i actually found a tarbomb but it's actually a zipbomb it was off a website tat was explaining what it does and how it works

the file is called "42.zip"

it's in lockdown right now and no i won't post it

---

