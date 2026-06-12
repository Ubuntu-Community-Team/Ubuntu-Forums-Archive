---
title: "Folder permission"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2007-03-17
extremely new to linux.  how do i give myself access to this file /Desktop/jre1.5.0_11

---

### Post by taurus on 2007-03-17
Are you talking about /Desktop/jre1.5.0_11 or ~/Desktop/jre1.5.0_11?

Applications -> Accessories -> Terminal
```
cd ~/Desktop/jre1.5.0_11
-or-
cd /Desktop/jre1.5.0_11
```

---

### Post by aysiu on 2007-03-17
Read these two links.

**Understanding Software Installation in General**:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

**Installing Java in Particular**:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by poordamnedfool on 2007-03-17
no the problem is that i do not have rights to modify the folder

---

### Post by taurus on 2007-03-17
Which directory, /Desktop/jre1.5.0_11 or ~/Desktop/jre1.5.0_11?

---

### Post by poordamnedfool on 2007-03-17
pretty sure it is ~/Desktop

---

### Post by aysiu on 2007-03-17
Well, you've got two separate issues here.

1. **Permissions**
I don't know how you lost permission to your own desktop, but you can probably get it back by typing this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *poordamnedfool:poordamnedfool* ~/Desktop
``` Substitute in your actual username for *poordamnedfool*, of course.

2. **Installing Java**
Forget about the file you downloaded. Read the links I posted before.

---

