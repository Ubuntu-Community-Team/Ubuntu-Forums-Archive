---
title: "How to break a running command"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-06
To remove a directory  and all its contents, I type (e.g.)

rm -r /home/user1/directory1

Now, it asks me to confirm deletion of each single file. Supposing there are 100 files, no one would like to do this. I know I might look for an option whch allows me to delete without the hassle of confirmation.

But my question is, once it starts asking me to delete one by one, how do I break the process. In windows, we use Ctrl+Break for such. In Ubuntu, the easiest I have been doing is to close the shell (using the x on top) then re-open.

Isn't there a keyboard combination to terminate?

---

### Post by taurus on 2006-03-06
```

<Ctrl>c

```
However, if you don't want the system to ask you, then use
```

rm -rf /home/user1/directory1

```

---

### Post by AtinLango on 2006-03-07
Thanx.

---

