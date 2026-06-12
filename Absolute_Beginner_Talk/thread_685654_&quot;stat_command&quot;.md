---
title: "&quot;stat command&quot;"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by browning_man9 on 2008-02-02
Hello. I'm attempting to use the stat command to get at the last modification time of a file since the epoch. The manual says that the "valid format sequence" for this is %Y. My question is what is the proper syntax. It's not like "stat -%Y file.txt." I'm using it to write a shell script to compare modification times. I thank you for your help!

---

### Post by browning_man9 on 2008-02-02
no ideas?

---

### Post by Nythain on 2008-02-02
try
```

stat --format=%Y whatever.txt

```
just pulled it from the man page

---

