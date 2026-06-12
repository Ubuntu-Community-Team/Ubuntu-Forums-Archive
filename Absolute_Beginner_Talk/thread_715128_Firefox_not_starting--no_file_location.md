---
title: "Firefox not starting--no file location?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by stropyboy11 on 2008-03-04
I was trying to update my Firefox to the Firefox 3 Beta 2, but I totally messed it up. After I messed up the install, I was hit with this message:

"Could not launch application

Failed to execute child process "firefox" (No such file or directory)"

So then I went to the Synaptic Package Manager and completely wiped out Firefox and reinstalled it, but it was to no avail, cause I keep getting the same message. Anyone have any idea??

-Stropko

---

### Post by stropyboy11 on 2008-03-04
Please help, I really need some advice...

---

### Post by lswest on 2008-03-04
try this
```
sudo aptitude remove --purge firefox firefox-3.0
sudo aptitude install firefox
``` in the terminal  should completely remove firefox 2.0 & 3.0 and then re-install firefox 2.0

---

### Post by stropyboy11 on 2008-03-04
Tried it, no good...still get same message...

Any more ideas?

---

