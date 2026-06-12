---
title: "mkdir doesnt work?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by someguy91 on 2007-06-25
I'm trying to make a directory in a mounted partition just to test.... so it was mkdir xxxxxxx but it told me i dont have permission. to make a directory? wth?

Thanks guys

---

### Post by kevdog on 2007-06-25
Try prefacing the command with sudo mkdir ...

If you ls -la the mounted directory, it will list the read,write,execute bits, along with user and group ownership.  Its likely you are not part of the group ownership.

Just a guess..

---

### Post by koshari on 2007-06-25
is the maount mounted with write permissions?

---

### Post by phidia on 2007-06-25
Try "sudo mkdir xxxxxxxx" without the quotes of course.

---

### Post by tbasherizer on 2007-06-25
It could also be an ntfs thing. Make sure you have the settings in NTFS Configuration tool set to read from Externlal and Internal Devices to be sure.

---

