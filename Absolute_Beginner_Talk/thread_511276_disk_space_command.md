---
title: "disk space command"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by jeff00z28 on 2007-07-27
whats the command to check disk space/usage

---

### Post by jeff00z28 on 2007-07-27
nevermind df -h

---

### Post by Rocket2DMn on 2007-07-27
du is the command you are looking for
```
du -h
```
df performs a similar function (free space), and requires the mount point as an argument
for more details:
```
man df
man du
```

---

### Post by RedSquirrel on 2007-07-27
Try:

```
df -h
```

---

