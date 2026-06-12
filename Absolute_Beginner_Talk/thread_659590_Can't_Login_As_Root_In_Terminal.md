---
title: "Can't Login As Root In Terminal"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by x02flash on 2008-01-05
Hello, I was trying to log into the root account through terminal while trying to install a file, which worked fine yesterday.  Now when i try to log in using "su" or "su -m" I get this error message

```
alex@alex-laptop:~$ su -m
Password: 
su: Authentication failure
Sorry.
alex@alex-laptop:~$ 

```

I know my password is correct, as it works when i go to open something like Synaptic and it needs me to authenticate, and this is the 9th or 10th unsuccessful try.  I've rebooted the system twice now and there's still no difference.

Anyone know a fix?

Thanks in Advance

---

### Post by Dr Small on 2008-01-05
Use:
```
sudo su
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by speedingbullet on 2008-01-05
Did you try sudo?

---

### Post by x02flash on 2008-01-05
Yep that works.  Thanks guys

---

