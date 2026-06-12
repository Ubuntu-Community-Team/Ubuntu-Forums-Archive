---
title: "Help! Software Updates..."
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-09-15
Yeah, so I was wondering if there's a way to delete/remove certain updates from the Software Updates thing. Like, I don't want to update my nVidia X.Org thing, because I know that it will **** up my computer, but I can only uncheck the box. I want to completely remove it from the updates so I don't have to see it again and uncheck it.


Thanks

---

### Post by Najand on 2006-09-15
Maybe command:
```

sudo aptitude hold <PACKAGENAME>

```
can help you.

---

### Post by ajgreeny on 2006-09-15
If you use synaptic you can lock the version of any package you have already installed.  I presume this must work through apt so should also stop the updater doing the deed as well, but I do not know that for sure so check further before assuming this is fact.

---

### Post by kbsuperstar on 2006-09-15
I'll have to try that command.

But, how do I lock packages in Synaptic? And how do I know what <PACKAGENAME> is?

Thanks

---

### Post by Najand on 2006-09-15
I am sure you know it when it asks you for upgrading. Don't you?

---

### Post by kbsuperstar on 2006-09-15
How do I lock the version I have now in Synaptic?

---

### Post by ajgreeny on 2006-09-17
Open synaptic, highlight the package you want to lock version, go to "Package" menu and click "Lock Package".  It's as simple as that!

---

