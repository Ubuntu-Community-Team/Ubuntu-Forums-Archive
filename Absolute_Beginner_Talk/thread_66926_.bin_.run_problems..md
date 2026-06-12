---
title: ".bin .run problems."
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by AlainRaymond on 2005-09-18
Hello. I'm really new to both Linux and Ubuntu. I've been having some problems installing the Java Runtime Library or Environment for Azureus and the drivers for my ATI Radeon 9550 Guru. They are both .bin and .run files and I can't seem to get them to run. I've tried using ./"filename" in root mode, yet it responds with "permission denied". I'd really like to know how to get them to run, since both seem as very common installation extensions, Any help would be appreciated! (I read a thread with a similar problem yet I couldn't grasp the answer to my query) Thanks in advance!

---

### Post by Xian on 2005-09-18
First please make sure that you have made those files executable.
Then your install procedure should work.

```
# sudo chmod a+x filename.bin
```

---

### Post by AlainRaymond on 2005-09-18
Oh great it worked just fine after that! Thank you very much!! It really seems like I'm a newcomer.

---

