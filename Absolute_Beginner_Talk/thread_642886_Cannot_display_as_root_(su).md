---
title: "Cannot display as root (su)"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by age99 on 2007-12-17
Hi,
I've just installed Ubuntu 7.10, and I have set up a user.  When I log in as root with the command "su -" from the terminal i cannot display any of the GUIs (ex: nedit or gedit).

Can anybody give me a hand?

Thanks

---

### Post by lgambett on 2007-12-17
Try to use sudo <command> instead of su -

---

### Post by sisco311 on 2007-12-17
To start a root shell, use:
```
sudo -s
```or
```
sudo -i
```[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by age99 on 2007-12-17
Thanks for the help.  The sudo -s worked great.

---

