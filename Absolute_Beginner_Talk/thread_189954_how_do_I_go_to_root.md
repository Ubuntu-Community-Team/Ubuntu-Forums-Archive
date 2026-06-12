---
title: "how do I go to root?"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by ph7klw on 2006-06-05
How do I go to root?

---

### Post by tkjacobsen on 2006-06-05
root is disabled by default in ubuntu. You should use sudo instead. Else take a look in the wiki: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by meng on 2006-06-05
The safest way is to preface each command that needs root authorization with "sudo"
If you really must, you can "sudo -i"
ubuntu.wiki.com/RootSudo

---

### Post by Burke on 2006-06-05
Type:
```
sudo passwd root
```
to set a root password, then type 'su' to switch to the root user for the rest of the terminal session or until you type exit.

---

### Post by fer5437 on 2006-06-05
You can use sudo -s

---

