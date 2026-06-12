---
title: "sudo su"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by panurge77 on 2006-06-23
Well, I guess lots of people miss the 'su' command when they first get into ubuntu. I always use the 'sudo su' way when I don't want to go typing tons of sudo's. It's a trick I learned when using osx. I never saw anyone talking about this on the forums, and it's not on Ubuntu guide. Is there a reason not to use 'sudo su'? Or a better approach for getting into root?

---

### Post by aysiu on 2006-06-23
I've seen ```
sudo -s
``` recommended a bit.

Frankly, I don't have any problem just using *sudo*.

---

### Post by BugenhagenXIII on 2006-06-24
If I need root for many commands, I just use 

```

sudo -i

```

---

### Post by aeto on 2006-06-24
for some reason, if i just typed su, "authentication failure". sudo -i works flawless.

---

### Post by DirtDawg on 2006-06-24
Could you make an alias? like:
```

alias su='sudo su'

```
Or maybe this would be a bad idea as it might cause some kind of conflict?

---

