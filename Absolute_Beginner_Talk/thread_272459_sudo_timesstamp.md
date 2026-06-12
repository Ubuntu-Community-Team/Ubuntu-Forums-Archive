---
title: "sudo timesstamp"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-10-06
nan@poc:~$ sudo apt-get install wine
sudo: timestamp too far in the future: Oct  6 17:45:47 2006


what the hell? It wont let me install anything at all. ](*,)

---

### Post by mitch.c on 2006-10-06
> **jcrnan said:**
> nan@poc:~$ sudo apt-get install wine
sudo: timestamp too far in the future: Oct  6 17:45:47 2006


what the hell? It wont let me install anything at all. ](*,)
Try:
```
sudo -k
sudo apt-get install wine
```

This will remove the current timestamp, and require you to enter your password again, effectively resetting sudo.

---

### Post by jcrnan on 2006-10-06
thanks a lot :)

---

