---
title: "Limewire won't close"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-04-21
I just installed Limewire but it wont close. Is there code that i could put in the Terminal to close it or something like that

---

### Post by marko_4454 on 2007-04-21
> **microsoft92sucks said:**
> I just installed Limewire but it wont close. Is there code that i could put in the Terminal to close it or something like that

yea, its called "kill"
just type in terminal
```
top
```

Look for the process called "java" and remember the Process ID (in the left column) Press control+C
This will return you to the prompt:
not type;
```
sudo kill <Process ID>
```
That should do it :)

---

### Post by microsoft92sucks on 2007-04-21
Thank u that worked perfactly. But do u know y it wouldent close?

---

