---
title: "What's the process name of update manager?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-08-05
In Xubuntu, what's the name of the process of the update manager?  I just can't spot it in the xfce4-taskmanager. Thanks.

---

### Post by felicity on 2007-08-05
Do you mean 'update-notifier'?

---

### Post by Blofeld on 2007-08-05
Can't be as when I have update manager running, nothing named "update"-anything shows up in the task manager.

---

### Post by walkerk on 2007-08-05
> **Blofeld said:**
> Can't be as when I have update manager running, nothing named "update"-anything shows up in the task manager.

```
ps -e | grep update
```

---

### Post by Blofeld on 2007-08-05
> 14132   ?   00:00:09   update-manager
Thanks, Walker.
So the taskmanager doesn't show all running processes even though I have ticked "Show own / system / all processes".  Lovely.
You know, what I like about computers is their extreme predictability.  The way they will ALWAYS EXACTLY UNFAILINGLY SLAVISHLY do as told.

---

