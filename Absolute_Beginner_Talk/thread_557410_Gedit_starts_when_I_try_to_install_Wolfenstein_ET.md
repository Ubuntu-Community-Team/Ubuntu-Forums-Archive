---
title: "Gedit starts when I try to install Wolfenstein ET"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by miyamotofreak on 2007-09-22
I'm installing a downloaded Wolfenstein .run file and when I type sudo sh "./et-linux-2.60.x86.run" it opens up gedit instead of a gui for tor Wolfenstein.

---

### Post by RomeReactor on 2007-09-22
Hi. That's weird; try making the file executable before running it:
```
chmod +x et-linux-2.60.x86.run
```
and then run it without **sh** and the quotes, like so:
```
./et-linux-2.60.x86.run
```

---

### Post by miyamotofreak on 2007-09-22
The quotes were the problem thanks.

---

