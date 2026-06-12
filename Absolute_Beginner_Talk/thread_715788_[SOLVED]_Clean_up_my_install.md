---
title: "[SOLVED] Clean up my install"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by computermesh on 2008-03-05
Is there a way to clean up everything that installed/or has been downloaded with Ubuntu. There's things that came with it I'm sure at least for the time being I will not be using since I'm a new user not even a day old. Is there a listing somewhere that has the "required" elements of Ubuntu. So I know what not to remove.

---

### Post by chacham23 on 2008-03-05
You can use Saynaptic manager.. or this link:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
If you want to remove programs that u dont use you can use also: Applications->Add/Remove

Assaf Chacham

---

### Post by Oldsoldier2003 on 2008-03-05
> **computermesh said:**
> Is there a way to clean up everything that installed/or has been downloaded with Ubuntu. There's things that came with it I'm sure at least for the time being I will not be using since I'm a new user not even a day old. Is there a listing somewhere that has the "required" elements of Ubuntu. So I know what not to remove.
from the terminal:
```
sudo apt-get clean
```
this will remove all of your cached packages, so if you try to reinstall an app you'll re download the package. this can restore a fair amount of space if you have intsalled a lot of new packages.

---

