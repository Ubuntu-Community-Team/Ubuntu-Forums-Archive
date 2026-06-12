---
title: "Conky staying default even though I've edited the config"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Ludford on 2008-01-17
I've edit the config file conkyrc. But it still displays the default white version halfway off my screen. Is it not listening to the config file or something?

---

### Post by Mikes80 on 2008-01-17
Have you tried logging in and out of X. You need to do this for the file to be read.

---

### Post by Ludford on 2008-01-17
Yeah, I've done it a few times aswel as restarting.

---

### Post by Mikes80 on 2008-01-17
Just installed and tried it. (Was using conky on ArchLinux last). It worked for me.
I may be stating the obvious but have you save conkyrc as conkyrc or **.**conkyrc.
Also it needs to be in your home folder. Sorry again for stating the obvious but, it's all I can think of. :)

---

### Post by SOULRiDER on 2008-01-17
Im not 100% sure if killing X will actually kill conky. Kill conky manually, just in case
```
killall conky
```

---

### Post by cmittle on 2008-01-17
What are you trying to change in the file?  Maybe it's not liking the syntax you used?  Did you reopen the .conkyrc file to ensure that the changes you made were saved?

---

### Post by Mikes80 on 2008-01-18
Post your .conkyrc then we can have a look.

---

