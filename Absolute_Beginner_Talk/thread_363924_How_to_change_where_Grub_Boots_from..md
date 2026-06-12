---
title: "How to change where Grub Boots from."
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by wedge421 on 2007-02-17
I have Ubuntu Dapper installed on an IDE HDD and Ubuntu Edgy installed in an SATA drive.  The problem is my Grub boots from my IDE with Dapper on it. What I want to do is format the IDE drive with Dapper on it and just run Edgy.  How can I tell Grub to use the SATA drive instead of looking for the Grub on the IDE drive with Dapper? My dapper drive is hdb1 and my Edgy drive is sda1. ANy help is much appreciated.

---

### Post by rsambuca on 2007-02-17
What is on hda?

---

### Post by wedge421 on 2007-02-19
It would have to by me Ubuntu 6.06 install. Can anyone help?

---

### Post by rsambuca on 2007-02-19
Open a terminal from either OS and enter this```
sudo grub
```

at the grub> prompt, enter```
find /boot/grub/stage1
``` and post the output here.

---

