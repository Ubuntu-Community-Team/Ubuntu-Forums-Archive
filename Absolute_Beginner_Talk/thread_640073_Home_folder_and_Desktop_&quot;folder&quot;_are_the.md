---
title: "Home folder and Desktop &quot;folder&quot; are the same!"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2007-12-13
:mad: !, i didn't do anything other than update a while ago and now anything I put into or delete out of the homefolder or desktop happens to the other. WHY ? its like they are merged, I dont do anything other than use pidgin and firefox and then this happened.:confused:

---

### Post by ectospasm on 2007-12-13
> **Hmarroqu said:**
> :mad: !, i didn't do anything other than update a while ago and now anything I put into or delete out of the homefolder or desktop happens to the other. WHY ? its like they are merged, I dont do anything other than use pidgin and firefox and then this happened.:confused:


I would double-check that the Desktop directory isn't a symlink to the /home/<user> directory.  That would explain the behavior you're seeing.

---

### Post by hfranco on 2007-12-13
Go to your /home directory and type:

```
ls -l
```

and then go into your /home/user directory and type the same thing.

These two folders might have a symbolic link referenced to each other

[http://en.wikipedia.org/wiki/Symbolic_link]("http://en.wikipedia.org/wiki/Symbolic_link")

---

### Post by xX_JIMI_Xx on 2007-12-26
i am experiencing the same.

theres also something on the home folder icon and im not sure what it is (see attachment).

it seems the desktop and home folder do have a sybolic link, and i would like to remove this link, so if anyone has any pointers on how to go about this i'd appreciate it.

---

