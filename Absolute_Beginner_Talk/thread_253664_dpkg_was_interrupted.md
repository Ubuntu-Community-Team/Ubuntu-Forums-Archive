---
title: "dpkg was interrupted?????"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by hc2995 on 2006-09-08
ok i tried to do sudo apt-get install but i got this instead:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

i did ./dpkg --configure -a and got this:

bash: ./dpkq: No such file or directory


how do i fix this?!?!?!?!

---

### Post by hc2995 on 2006-09-08
Help Me Please!

---

### Post by bodhi.zazen on 2006-09-08
Typo error.

it's is dpkg (with a "g") NOT dpkq (with a "Q")

Perhaps
```
sudo dpkg --configure -a
```

either that you you mis posted you error message.

---

