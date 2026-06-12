---
title: "SSH logging"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by revdev on 2006-05-17
Does anyone know how to change SSH logging so that it not only logs connections and failed login attempts, etc., but also logs any commands that a logged in user runs? Is this possible?

Thanks

---

### Post by xtacocorex on 2006-05-17
I'm not sure how to do it exactly, but I know that you can check a users .bash_history file to see the commands they use. It won't give them a time that it was run, but it'll give you an idea of what they were doing.

I know thats what my team and I did during a cyber defense competition. 

Each user's .bash_history file is set to:
```
-rw-------   1 bobw bobw   6496 2006-05-16 21:45 .bash_history

```

You can either read it as the root user under sudo or change the permissions to allow it to be read by anyone.

---

