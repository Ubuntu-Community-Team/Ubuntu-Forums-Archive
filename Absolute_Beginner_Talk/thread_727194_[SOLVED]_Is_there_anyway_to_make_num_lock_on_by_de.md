---
title: "[SOLVED] Is there anyway to make num lock on by default at start up?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by HighlyCalculated on 2008-03-17
Is there anyway to make num lock on by default at start up on Xubuntu?

I know it's trivial, but I'm so used to it being always on.  I keep trying to use my number pad and wondering what the heck is going on....

---

### Post by herbster on 2008-03-17
Have you checked your BIOS? There's usually an option in there. Actually, I believe there always is.

---

### Post by bollix47 on 2008-03-17
You could install numlockx using synaptic or:

```
sudo apt-get install numlockx
```

---

### Post by HighlyCalculated on 2008-03-17
Thanks bollix.

Herbster, there was no option in my BIOS.  Maybe it's because it's such an old system I'm running.

---

### Post by drs305 on 2008-03-17
There is also an option via gconf-editor to remember the last state of the numlock key or to have the numlock on as default. In terminal, open "gconf-editor" then  Edit, Find (check 'Search also in key names") for 'numlock' for the applicable settings to check.

---

