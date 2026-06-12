---
title: "Sun Java problems :( [Help needed]"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by -Soul_Reaper- on 2007-05-30
I have recently installed Ubuntu (:D:KS:popcorn:), so i am trying to find out how to install java, i tried a few sites, none helped. I was wandering if i needed a specific version of it for Ubuntu, or if i needed a different program to use the '.bin' file type. If anyone has a link for a simple tutorial/instructions that would be great.
Thanks. :D

---

### Post by bollix47 on 2007-05-30
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by -Soul_Reaper- on 2007-05-30
Doesn't work! Maybe i read it wrong,

---

### Post by taurus on 2007-05-30
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-fonts
java -version
```

---

