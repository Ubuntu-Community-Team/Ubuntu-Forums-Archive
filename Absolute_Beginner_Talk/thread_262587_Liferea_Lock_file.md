---
title: "Liferea Lock file"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by iampoch on 2006-09-21
I was unable to shut down my computer last night. When I opened it this morning everything went fine except for Liferea as it was unable to remove the lock file. How do I manually remove it? I dont know where it is.

---

### Post by reacocard on 2006-09-21
it's in

```
/home/yourusername/.liferea/lock
```

so just use

```
rm ~/.liferea/lock
```

to delete it.

---

### Post by iampoch on 2006-09-23
> **reacocard said:**
> it's in

```
/home/yourusername/.liferea/lock
```

so just use

```
rm ~/.liferea/lock
```

to delete it.

Got it, it worked! :D thsnks :D

---

