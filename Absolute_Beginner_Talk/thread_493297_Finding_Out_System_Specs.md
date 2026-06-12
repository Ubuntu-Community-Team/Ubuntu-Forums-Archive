---
title: "Finding Out System Specs"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by chessercizes on 2007-07-05
Hey everyone!

Im pretty new to ubuntu, so im lost as to how to do this.

Recently I got a junk computer from someone that didnt want it. So when i tried to boot up windows wasnt working; which was fine, since i wanted ubuntu neways. I installed ubuntu and all that.

Is there any way to find out the system specifications (i.e. amount of ram, processor speed, motherboard, etc.)? I looked at hardware information under System>Preferences, but i couldn't make head or tail of it.
Is there an easy way to see the system specifications?

any help would be uberly appreciated.

thanks a million

---

### Post by apunc1 on 2007-07-05
```
dmesg |more
```

```
lspci
```

---

### Post by reset3x on 2007-07-05
> **chessercizes said:**
> Hey everyone!

Im pretty new to ubuntu, so im lost as to how to do this.

Recently I got a junk computer from someone that didnt want it. So when i tried to boot up windows wasnt working; which was fine, since i wanted ubuntu neways. I installed ubuntu and all that.

Is there any way to find out the system specifications (i.e. amount of ram, processor speed, motherboard, etc.)? I looked at hardware information under System>Preferences, but i couldn't make head or tail of it.
Is there an easy way to see the system specifications?

any help would be uberly appreciated.

thanks a million

open a terminal and enter sudo lshw....

---

### Post by chessercizes on 2007-07-05
thanks very much, it really helped.

also, i later found 2 programs called sysinfo hardinfo which does the same thing really well too.

thanks though
 :)

---

