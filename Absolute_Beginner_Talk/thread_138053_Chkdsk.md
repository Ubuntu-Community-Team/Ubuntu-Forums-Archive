---
title: "Chkdsk"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by My-dial-up on 2006-03-01
OS: Ubuntu 5.10 in Terninal mode.

In the old days of MS-DOS we had a program called chkdsk which displayed the HDD current usage & free space. Is there a Ubuntu version?

---

### Post by Jucato on 2006-03-01
```
df -l
```
or ```
df -lh
```
to display it in human readable form (GB instead of bytes_

---

### Post by tmahmood on 2006-03-01
There supposed to be a tool named du to do this...

---

### Post by Jucato on 2006-03-01
[QUOTE=tmahmood]There supposed to be a tool named du to do this...[/QUOTE]

no. du summarizes the memory usage of files. somewhat like ls -l (or ls -lh) except it only displays file sizes.

---

