---
title: "Sporadic Freezing, Not allowing to update"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Billybb347 on 2007-03-03
I had instaled 6.06 and was updating (not to 6.10 but just updates)when it froze about 2 sec. from the end. I rebooted hoping that the updates went through( I don't thikn they did) when I rebooted i tried to start the updater it said it was already runing. I f I try to install anything It says that the updater is running and i have to stop it to install that something. And at random times it has been freezing, no response to anything I do exept hardbooting. I think the freezing will stop if I update.

[[IMG]http://img169.imageshack.us/img169/309/screenshotik7.th.png[/IMG]](http://img169.imageshack.us/my.php?image=screenshotik7.png)

---

### Post by mexlinux on 2007-03-03
I guess some package did not complete instalation, Try running:
```

sudo dpkg --configure -a

```
After that try your update

---

### Post by Billybb347 on 2007-03-04
Thanks alot worked perfectly. :)

---

