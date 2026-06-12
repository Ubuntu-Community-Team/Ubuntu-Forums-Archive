---
title: "Messed something up, need help fixing"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-11-01
Okay well I downloaded and installed Limewire today after numerous failed attempts with the Frostwire connection. Well I had it up and running and had been using it. But when I took the .sh out of the folder that was extracted and put it onto my desktop and changed the name, it stopped working. It will only open up to the source code now. I can't even remember what the file was called so I can't run it from the terminal (especially if I moved it and changed the name). What should I do?:confused:

---

### Post by taurus on 2006-11-01
Download and install it again!!!

---

### Post by voodoonirvana on 2006-11-01
> **taurus said:**
> Download and install it again!!!

Aaaawww!](*,)  That's my only option?! Oh well, I guess I learned from my mistake. But which was the one that messed it up; the actual move of the file, or the name change?

---

### Post by taurus on 2006-11-01
The move of the file.  If you want to move it somewhere else, then create a link to it so the program can find it...

---

### Post by voodoonirvana on 2006-11-01
> **taurus said:**
> The move of the file.  If you want to move it somewhere else, then create a link to it so the program can find it...

How would I go about creating a link? And one more question, why doesn't a link get put into the Applications? :confused: Most other things do...

---

### Post by taurus on 2006-11-01
```

ln -s filename destination
-or-
man ln

```
If you install something in your own home directory, then you need to create a menu in Applications yourself...

---

### Post by voodoonirvana on 2006-11-01
Thanks for the help Taurus! :)

---

### Post by taurus on 2006-11-01
> **voodoonirvana said:**
> Thanks for the help Taurus! :)
No problem.  You can always create a link to your problem in the panel if you install it in your $HOME directory.  Then, you just double-click to run it.

---

