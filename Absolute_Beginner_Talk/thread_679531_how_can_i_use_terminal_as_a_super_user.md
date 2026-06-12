---
title: "how can i use terminal as a super user?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by henry8596 on 2008-01-27
i am trying to install vmware under ubuntu on my macbook
however, it said i need to be a super user in order to install
how can i use terminal as a super user?

---

### Post by LaRoza on 2008-01-27
Type "sudo" before the command you need to run as root.

```

sudo apt-get update

```

Use gksudo for GUI apps.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2008-01-27
Or, if you have multiple commands you want to run as root, you can save yourself some typing by using ```
sudo -i
```

---

### Post by polmir on 2008-01-27
Only type in terminal:
```
sudo su 
```
 or 
```
sudo su -
```
your password (hidden) <enter>

good luck

<<My Linux is better for my English>>

---

