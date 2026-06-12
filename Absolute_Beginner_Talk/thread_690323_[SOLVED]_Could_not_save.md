---
title: "[SOLVED] Could not save?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-02-07
Okay so I'm doing the thing for "how-to awn curves" and theres what part where it opens the sources.list file and I have to add two lines to the bottom, I add the two lines to the bottom and it tells me in the guide that I have to save and close it, when I try to save it it says this...

**[COLOR="Lime"]_You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again._[/COLOR]**

How do I fix this?

---

### Post by jan quark on 2008-02-07
```
gksudo gedit /etc/apt/sources.list
```

now you have the permission

---

### Post by phr0ze on 2008-02-07
Use Sudo in the command to open sources.lst

Example:

sudo command

Then type your password.

---

### Post by blasteryui on 2008-02-07
> **jan quark said:**
> ```
gksudo gedit /etc/apt/sources.list
```

now you have the permission

Thanks a lot friend.

---

### Post by jan quark on 2008-02-07
you are welcome

always ask we are here to help,,, when we can :)
pls mark this thread as solved see signature

---

