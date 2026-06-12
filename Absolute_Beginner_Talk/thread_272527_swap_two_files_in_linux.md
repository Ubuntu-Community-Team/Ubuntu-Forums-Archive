---
title: "swap two files in linux"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by neumeka on 2006-10-06
Is there a command to swap the contents of two files?  For example, if fileA contains "foo" and fileB contains "bar", is there a single command that would allow me to put "bar" in fileA and "foo" in fileB?

---

### Post by steve.horsley on 2006-10-06
I don't think so. The closest I can think of is:
**mv fileA tempFileName ; mv fileB fileA ; mv tempFileName fileB**
but that's cheating - it's three commands.

---

### Post by jd65pl on 2006-10-06
Can't you just rename the files as appropriate to get this effect?

---

### Post by neumeka on 2006-10-06
I could just rename them as appropriate, but it seems like there would be a liunx command or easier way to do it than renaming.

---

