---
title: "Staring two threads of a same process"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by unbuntued on 2008-01-28
What I want to do, is have two instances of a process running.
For example, I want two Firefox instances. And if one of them crashes, the other doesn't. I recall there's a shell command that does that. But can't remember what it was...

---

### Post by rax_m on 2008-01-28
After you've opened the first instance of FF just click the FF icon again and a second instance will open up. As long as you DO NOT use the File->New Window option in FF it should be completely seperate. 

Unless you want to do it in one command?

---

### Post by unbuntued on 2008-01-28
This will open two Firefox windows, I understand that. But if one of the window crashes (because obviously Firefox crashes sometimes), the other one will crash too because it's the same Firefox process.

What I want is two completely distinct Firefox processes to run simultaneously, independent of each other.

That is when you check running processes through ```
ps -ax | grep firefox
```
You get two entries.

The command I'm looking for (to be ran from the terminal) looks like something like that, I think.
```
firefox &something_here
```

---

### Post by emarkd on 2008-01-28
Well, you've almost got it.  Try:

```
firefox & firefox
```

---

