---
title: "slow down problem"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-02
I Ran cmd. "cat /etc/fstab|grep swap" and got "UUID=6c54f551-e171-415e-a066-1f33cefad0f0 none swap sw 0 0" what does this mean?

---

### Post by yabbadabbadont on 2007-06-02
That you have a swap partition that is activated during boot.  ;)

Edit: In a terminal window run, "man fstab", without the quotes for details.  You will also need to read the "mount" manpage probably.

---

### Post by swoll1980 on 2007-06-02
can i get a complete manual some were?

---

### Post by yabbadabbadont on 2007-06-02
[http://www.linuxquestions.org/linux/answers/Hardware/etc_fstab_broken_down_and_explained](http://www.linuxquestions.org/linux/answers/Hardware/etc_fstab_broken_down_and_explained)

That may be a bit easier to process.  ;)

---

