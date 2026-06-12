---
title: "Hamachi error"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2006-09-29
> alex@alex-desktop:~$ hamachi start
Cannot access lock file /home/alex/.hamachi//.lock
I have no idea what to make of this.

And gHamachi says:
> Hamachi could not be started...

What is this lock file and how do I fix this error?

I tried posting in the Hamachi Linux forum but it's dead.

---

### Post by jpkotta on 2006-10-01
```
hamachi stop
mv ~/.hamachi hamachi.bck
hamachi-init
hamachi start

```

Should create a new ~/.hamachi.  If the new one works, then just delete the backup.

Lock files are used to make sure two programs don't try to modify the same thing at the same time.

---

