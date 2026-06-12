---
title: "[SOLVED] munin package problems"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by getut on 2007-11-18
My generic question is: Is there a way I can force a complete package removal and reinstall from scratch?

Specifically, I'm having a problem with the munin and munin-node packages. I did an install and had it working but wanted to tweak the output by getting rid of some of the graphs that I wouldn't need.

Well the real problem begins there. I messed it up pretty badly and decided to get a fresh start. I ran a "sudo aptitude remove --purge munin munin-node" thinking that the --purge was supposed to get rid of **everything**. Well it didn't, so I manually searched and destroyed all remaining folders with munin in the name.

I retrieved and installed the packages again and got an install error for munin-node. I finally got that one worked out and the install SAYS it completes successfully, but there are still many munin files missing such as the symbolic links created specifically for each system (probably some script failing to run that creates those) after it says it finished the installs completely.

How can I do a fresh install and guarantee that all scripts associated with the installation also run?

---

### Post by Qwerty_ on 2007-11-18
I am not sure if this will make much of a difference on what you already tried, to remove the software.

```
 sudo dpkg -r munim
```

---

### Post by getut on 2007-11-19
Well it seems for the second or third time I got burned by the difference between aptitude and apt-get.

No amount of aptitude install and aptitude remove --purge fixed the issue. It still never put some of the files back in that it did in the original install that also was done with aptitude.

I switched over to apt-get and did a remove --purge with it and then the subsequent install with apt-get, voila... all the missing files were there.

---

