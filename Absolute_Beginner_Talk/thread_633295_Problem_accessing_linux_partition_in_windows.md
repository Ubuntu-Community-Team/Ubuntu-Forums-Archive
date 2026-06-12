---
title: "Problem accessing linux partition in windows"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by hrolfp on 2007-12-06
I installed the ext2 file system from [here](http://www.fs-driver.org/) and it worked fine for a long time so I could access all my files in my ubuntu partition in windows. For some reason it stopped working today, and anytime I try to access it I get the error "drive is not formatted. do you want to format it now?" Any idea what's going wrong?

---

### Post by banewman on 2007-12-06
Did you recently update/upgrade ?
That can bugger things up sometimes. :)

---

### Post by ReverendJ1 on 2007-12-06
Have you rebooted since it started not working? It could be that the Ext driver is not being started. Also, try to uninstall and reinstall the Ext2 IFS program. See if that helps. It is possible that the driver/program became corrupted somehow.

---

### Post by skymera on 2007-12-06
try:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by vikram on 2007-12-06
you sometimes get an error if the ext2 or ext3 volume was not unmounted cleanly. sometimes booting into linux shutting down cleanly and then booting into windows has solved the problem for me.

other times i have had to fsck the ext2/3 volume before i could use the ext2 driver

see diagnostic tool in the troubleshooting section
[http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)

---

