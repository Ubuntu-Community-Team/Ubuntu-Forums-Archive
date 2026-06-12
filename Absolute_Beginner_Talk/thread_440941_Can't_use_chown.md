---
title: "Can't use chown"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Pisi-Deff on 2007-05-12
I created a txt file under WinXP (like a notepad between OS's) and under Ubuntu it's owned by root. I want to chown it to my account, but i can't.
The file is called 'loemind.txt'
```
eerik@Eerik-Ubuntu:~$ sudo chown eerik:eerik /media/Files/loemind.txt
chown: changing ownership of `/media/Files/loemind.txt': Operation not permitted

```

---

### Post by ubnewbie2 on 2007-05-12
What is the filesystem on the device where this file is stored?  Maybe it doesn't support unix ownership.

---

### Post by Pisi-Deff on 2007-05-12
> **ubnewbie2 said:**
> What is the filesystem on the device where this file is stored?  Maybe it doesn't support unix ownership.
Oh, i didn't think of that... It's fat32, so it probably doesn't ...
Thanks :D

---

### Post by Najand on 2007-05-12
Can you copy and paste the following commands?
```

$ mount
$ ls /media/Files/loemind.txt -l

```

---

