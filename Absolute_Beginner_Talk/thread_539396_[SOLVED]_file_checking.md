---
title: "[SOLVED] file checking"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by DarinB on 2007-08-31
file check system occurs every 27 times but it seems to occur more often than that. how do i check if the system works ok
OR is it better to change the last digit in fstab to 0 and fsck myself. but i will forget. i am nervous about unmounting then check how do i unmount my only driva and then check it??????

---

### Post by overdrank on 2007-08-31
> **DarinB said:**
> file check system occurs every 27 times but it seems to occur more often than that. how do i check if the system works ok
OR is it better to change the last digit in fstab to 0 and fsck myself. but i will forget. i am nervous about unmounting then check how do i unmount my only driva and then check it??????

HI maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=537276](http://ubuntuforums.org/showthread.php?t=537276)

:popcorn:

---

### Post by DarinB on 2007-08-31
it seems that it is better to just leave it alone and not to mess with it, maybe just take note how many times i boot before the file check, 

Is it possible that it checks early .....if i shut down improperly.

---

### Post by por100pre1 on 2007-08-31
You can force fsck when you want to:

```
sudo touch /forcefsck && sudo reboot
```

---

### Post by DarinB on 2007-08-31
what about the unmounting before force fsck???
is it dangerous to the system???

---

### Post by overdrank on 2007-08-31
> **DarinB said:**
> what about the unmounting before force fsck???
is it dangerous to the system???

HI after searching and comparing the commands with ones used, that command is a forced fsck at the reboot of the system.

---

### Post by DarinB on 2007-08-31
thanks i will monitor and if i have problems i will 0 fstab and do it manually

---

