---
title: "sshd star up"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by timon_tg on 2006-11-20
can anyone advise me how to start sshd at boot up?

Ubuntu 6.10

---

### Post by carlosqueso on 2006-11-20
have you installed the openssh-server package?  Ubuntu doesn't have it installed by default.  Once you do that, it should come up automatically.

---

### Post by timon_tg on 2006-11-20
Yes , openssh-server package is installed , but is not starting automatically at boot up?

---

### Post by izmaelis on 2006-11-20
Try this
```
#sudo update-rc.d sshd defaults
```
and check if it's started on next bootup.

---

### Post by timon_tg on 2006-11-20
sudo update-rc.d ssh defaults
works great!
10x

---

