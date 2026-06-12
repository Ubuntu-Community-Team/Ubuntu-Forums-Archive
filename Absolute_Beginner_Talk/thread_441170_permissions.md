---
title: "permissions"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Timmy66 on 2007-05-12
How can I change permissions.I keep getting a message that says I don't have permissions to install anything.Is there an easy way to give myself permissions.

---

### Post by Najand on 2007-05-12
You should use one of 
```

chmod
chown

```
commands.
Check [http://tldp.org/LDP/intro-linux/html/sect_03_04.html](http://tldp.org/LDP/intro-linux/html/sect_03_04.html) to learn how to use them.

---

### Post by taurus on 2007-05-12
What do you plan to install?  Use sudo if you want to install something.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install **program_name**
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taurus on 2007-05-12
> **Najand said:**
> You should use one of 
```

chmod
chown

```
commands.

Please DO NOT change permissions of anything outside your $HOME directory because doing so could crash your machine beyond repair.  Use sudo instead.

---

