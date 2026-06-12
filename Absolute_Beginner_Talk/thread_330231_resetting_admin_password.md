---
title: "resetting admin password"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by madmax04 on 2007-01-02
New install and the guy does not remember the password. Only one user. How could we reset it or change it?

---

### Post by meng on 2007-01-02
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by taurus on 2007-01-02
Boot into recovery mode from GRUB menu and at the prompt, type

```
passwd **john**
(assuming **john** is his username...)
shutdown -r now
```

---

### Post by aysiu on 2007-01-02
Or, a slight modification of taurus' instructions, if you would rather reboot than shut down: ```
passwd *username*
reboot
```

---

### Post by taurus on 2007-01-02
> **aysiu said:**
> Or, a slight modification of taurus' instructions, if you would rather reboot than shut down: ```
passwd *username*
reboot
```

Actually, "**shutdown -r now**" will reboot right away while "**shutdown -h now**" will shut down/halt the machine...

---

### Post by aysiu on 2007-01-02
> **taurus said:**
> Actually, "**shutdown -r now**" will reboot right away while "**shutdown -h now**" will shut down/halt the machine...
You're right. I didn't read it carefully.

---

