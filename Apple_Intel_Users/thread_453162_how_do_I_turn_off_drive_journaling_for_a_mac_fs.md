---
title: "how do I turn off drive journaling for a mac fs?"
date: 2007-05-24
forum: Apple Intel Users
---

### Post by MatthewACT on 2007-05-24
how do I turn off drive journaling for a mac fs?

---

### Post by pouns on 2007-05-24
Hi ,
from here :
[http://modular.math.washington.edu/macbook/](http://modular.math.washington.edu/macbook/)

(i found this page with linux mac os X journalisation in google)

"Linux does not support HFS+ in write mode if the journalisation is
used. I had to remove journalisation ("diskutil disableJournal /"
under Mac OS X) to be able to write to my HFS+ partition."

By

---

### Post by benanzo on 2007-05-24
How to disable journaling of the Mac OS X HFS+ partition:

Either boot into OS X or boot to the Mac OS X install disk.

Open a terminal and type:
```
diskutil disableJournal disk0s2
```
It will print a message telling whether the command succeeded or failed.

*disk0s2* is the default partition OS X installs to, to find out for sure do:
```
diskutil list
```

---

