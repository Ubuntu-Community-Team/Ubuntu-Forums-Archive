---
title: "[SOLVED] Flash only loads on demand ff3b5"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by siraf on 2008-04-10
Hey all, I recently upgraded to hardy heron, and I've only had one 'weird' issue (weird meaning that it's probably easily solvable, but still annoying).
When I go to any site with flash content, instead of fully loading the flash content, firefox puts a 'play' button, and i need to click on it to start the flash player. I'm using firefox 3 b 5, and this seems to happen even with all of my extensions turned off. Now, I think it may have something to do with a totem extension I installed, but I'm not sure.
Any ideas on how to let flash load automatically?
Thanks for your help in advance.

---

### Post by scramasax on 2008-04-10
> **siraf said:**
> When I go to any site with flash content, instead of fully loading the flash content, firefox puts a 'play' button, and i need to click on it to start the flash player.

Could you post a screenshot?  Maybe someone would recognize what it is from that.

---

### Post by siraf on 2008-04-10
OK i found the fix, I was running two conflicting versions of flash, so I removed one:
```
sudo apt-get remove swfdec-mozilla 
```

---

