---
title: "two questions from a noob"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by janis44 on 2008-03-09
hello everyone! i installed ubuntu gutsy gibbon with xp the other day and everything went fine until the next time i booted my linux distro, my first question is (1) how to view my windows partition and files in ubuntu? it was there the first time but now its missing ( the drives of windows in my desktop). i like this feature at least for the mean time im learning ubuntu because i could readily access my video tutorials which by the way is in .exe. (2) i remember that i change my desktop wallpaper but again it was gone when i log on. thanks in advance for the help.:)

---

### Post by taurus on 2008-03-09
Did you shutdown windows cleanly the last time you used it?  Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

