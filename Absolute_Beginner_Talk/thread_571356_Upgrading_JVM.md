---
title: "Upgrading JVM"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-09
I just installed the java from the website and it is located at /usr/share/java/jrel.6.0_03.  I tried to start eclipse and says i still have 1.4.2 and i need 1.5 of the JVM.  if i did not upgrade the JVM then how do i upgrade the JVM?

---

### Post by FuturePilot on 2007-10-09
You need to tell your system you have installed a new version of Java
```
sudo update-alternatives --config java
```
Then pick the one that says Sun Java6

---

### Post by RyanZec on 2007-10-09
I tried that but the newly installed one does not show up

---

