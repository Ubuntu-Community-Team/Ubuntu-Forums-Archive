---
title: "Kernel version"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Strider42 on 2007-02-07
Hi,

How do I find out which kernel version I am running.  I ran the command sudo linux-686 from a terminal window, it returned without any errors, but I'm not sure how to check if that kernel is now installed and actually running.

Thanks in advance.

---

### Post by mcduck on 2007-02-07
run 'cat /proc/version' :)

---

### Post by Strider42 on 2007-02-07
Thank you!

---

### Post by fusiachi on 2007-02-07
Now, I'm pretty new at this, but ```
uname -a
``` should do it.

Edit: Beat to the punch.

---

### Post by r4ik on 2007-02-07
Guess what

uname -r

does :)

---

