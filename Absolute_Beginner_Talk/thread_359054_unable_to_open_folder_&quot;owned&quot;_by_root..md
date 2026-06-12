---
title: "unable to open folder &quot;owned&quot; by root."
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by timmins on 2007-02-11
Hi, I'm currently trying to install frostwire, as per the instructions I have to add a folder called usr/java/. I am unable to make this folder because the owner of this folder is root, and I am not him. How do I either log on as root and change the permissions or find another way to get around this problem?

Thanks very much

---

### Post by taurus on 2007-02-11
Applications -> Accessories -> Terminal
```
sudo mkdir /usr/java
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tbroderick on 2007-02-11
taurus was quicker

---

### Post by timmins on 2007-02-11
thanks alot.

---

