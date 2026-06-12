---
title: "rmdir\rm question"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-10-07
Is there anyway to remove a folder that is full?

I have a folder with like 5 other folders in side that i don't need and i have tried the ```
sudo rmdir --ignore-fail-on-non-emptry /usr/local/.....
``` but when i hit enter nothing happens and the files are still there.

---

### Post by aysiu on 2005-10-07
Have you tried *sudo rm -r /whateverthediris*?

---

### Post by nitricacid on 2005-10-07
That did the trick. 
Thanks alot :D

---

