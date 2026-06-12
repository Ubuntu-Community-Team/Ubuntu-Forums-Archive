---
title: "copying smb.img"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by SconiGuy on 2007-12-02
I'm need help copying the smb.img file to a floppy.
I tried "dd if=sbm.img of=/dev/fd0" 
but I get an error message that says "dd: opening 'smb.img' : no such file or directory" 
The img file was downloaded to the desktop.

Ubuntu 6.06 LTS Dapper Drake

Thanks SG

---

### Post by Dr Small on 2007-12-02
```
dd if=/home/`whoami`/Desktop/sbm.img of=/dev/fd0
```

---

### Post by SconiGuy on 2007-12-02
Thank you very much:)

---

