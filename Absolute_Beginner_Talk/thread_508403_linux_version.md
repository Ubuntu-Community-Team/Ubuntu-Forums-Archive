---
title: "linux version"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by dd1313 on 2007-07-24
hi guys

bought a used computer that has linux installed.

How do i check what version of linux is installed.I cannot see it on the desktop
It has the KDE desktop

Thanks
DD

---

### Post by 505 on 2007-07-24
If it is a Kubuntu version, press Ctrl+Alt+F2 and it should read "Kubuntu X.XX" that is your Kubuntu version. If you want to know the Linux kernel version, open a terminal and type "uname -a"

---

### Post by sad_iq on 2007-07-24
Or open a terminal and type ```
cat /etc/issue.net
```

---

### Post by Bachstelze on 2007-07-24
```
uname -r
```

might be enough to find out which distro you have.

---

### Post by sad_iq on 2007-07-24
> **HymnToLife said:**
> ```
uname -r
```

might be enough to find out which distro you have.
That only gives you the kernel version. **uname -a** gives more info but to see if he's using debian or fedora or whatever the /etc/issue.net holds the answer!!!

---

### Post by dd1313 on 2007-07-24
THanks GUys

DD

---

