---
title: "Certain Programs won't install"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by iv76erson03 on 2008-01-01
Sorry if this has been asked 1 billion times...I tried searching but didn't see it. I'm a second time user (installed 5.10 when it came out and didn't work for me) and I'm trying to add some programs with the add/remove programs thing. Some programs like Atlantik won't install and it says that it cannot be installed on my computer type (i386). I'm trying to figure out why I can't put these programs on my PC. I have 7.10 with an IBM Thinkpad. Thanks.

---

### Post by (((X))) on 2008-01-01
is your computer i386?

---

### Post by taurus on 2008-01-01
You need to enable more repos in /etc/apt/sources.list before you can install more stuff.  So, close down Add/Remove.  Then, click System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and place a check mark in front of all the lines except the last one, Source code and the CDROM at the bottom window.  Close it and press Refresh.  Now, you can try to install it again from synaptic or close down synaptic and run your Add/Remove again.

---

### Post by iv76erson03 on 2008-01-01
Capital! It worked right away. :)

---

