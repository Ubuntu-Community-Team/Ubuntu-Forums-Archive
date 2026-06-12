---
title: "Ubuntu Load Problem"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by mohajerx on 2007-12-12
Hello ,
Version : 7.10
I have Ubuntu And Windows xp installed.
When i Select Ubuntu for load from menu
Then only a black screen and nothing else.
And Ubuntu not load **since** i use ctrl + alt + f2
then ubuntu start loading and all things work fine for load.

how to to start with default "Ctrl+Alt+F2" for every ubuntu load ?

---

### Post by meborc on 2007-12-12
when in grub menu, press "e" ... then choose the kernel line and press "e" again... can you please post what is in the end of the line... i have a feeling that there is a vga=xxx that does not comply with the kernel... just a hunch, but if it is this, then it is easy to fix

(just hit enter and "b" to boot afterwards)

---

### Post by mohajerx on 2007-12-12
Thanks for reply.
result :
<2-aef6-some code here. ro quiet splash

also when i use ctrl + alt + f2 for load i see this line :
intel_rng : WHT Not Detected.

Load from live cd is fine.

---

