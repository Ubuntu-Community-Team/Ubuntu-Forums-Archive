---
title: "adding directory to PATH"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-08-09
How do I add a new directory to my PATH?

---

### Post by bensexson on 2006-08-09
The file /etc/environment add the directory you want to the PATH variable in this file.

---

### Post by Tomosaur on 2006-08-09
Actually, I find the best way is to add the following lines to ~/.bashrc

```

# add extra paths
export PATH=$PATH:<newPathHere>

```

For example, I have:
```

# add extra paths
export PATH=$PATH:/bin/java/jdk1.5.0_07/bin
export JAVA_HOME=/bin/java/jdk1.5.0_07

```

---

