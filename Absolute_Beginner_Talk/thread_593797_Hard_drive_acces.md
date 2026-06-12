---
title: "Hard drive acces"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Lightmaster on 2007-10-27
Hello fellow members!
I installed Xubuntu 7.04 and i stuck into a problem.I have Vista installed on two of my partitions, and on the third, i have Xp, wich i share with Xubuntu.I can't use the disks to save programs i'm installing with Wine, for ex.Anarchy Online, it says i cannot save there.Is there a way to solve this problem?

---

### Post by taurus on 2007-10-27
If you want to write to ntfs filesystem, you need to install ntfs-3g and use it instead of the default ntfs driver.

```
sudo apt-get update
sudo apt-get install ntfs-3g ntfs-config
gksudo ntfs-config
```

---

