---
title: "bash coloring - quick question"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2007-07-05
how do i modify the way bash displays tar.gz files?  i was able to set my normal shell to remove that green from my user prompt. It still shows up on the tar.gz files and i would like to remove that....


thanks

---

### Post by bulldog060 on 2007-07-05
check in ~/.bashrc for a line that says `alias ls='ls --color=auto' ' and remove it ... should take care of your problem.

~ron

---

