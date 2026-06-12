---
title: "Is there a way to edit fstab from the root command-line"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by deaster2 on 2007-09-07
I have installed a 2nd hard-drive, and something went wrong 
with my fstab file. My system won't boot now. I am at command
line "root@deaster-desktop". Is there a way to edit the /etc/fstab
file from this command line?  I ran 'gedit /etc/fstab' and get
'cannot open display'.

---

### Post by Outrunner on 2007-09-07
You need to use nano if you're not running X

```
nano /etc/fstab
```

---

### Post by deaster2 on 2007-09-07
Many thanks, Outrunner...

---

### Post by hyper_ch on 2007-09-07
and don't forget the "sudo" since the file is owned by root.

---

