---
title: "Verify that Java is in the user path"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by aphelps on 2007-04-29
How do I verify that Verify that Java is in the user path, and if it isn't, how do I add it?

---

### Post by taurus on 2007-04-29
```
java -version
```
To configure it, run

```
sudo update-alternatives --config java
```

---

