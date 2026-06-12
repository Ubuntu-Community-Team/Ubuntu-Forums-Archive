---
title: "Installing ATI drivers"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by JPDVM2014 on 2006-10-29
Hi,
   
  I'm trying to install the ati drivers on edgy, but when i go to load the kernel module it doesn't work. Well one command doesn't work. I'm following a tutorial and the first command it has is "sudo rmmod -f fglrx" when i do this i get an error. "ERROR: Removing 'fglrx': No such file or directory" Is this normal or is something wrong? Thanks.

EDIT:
Nevermind. I fixed it. I did a full system restart instead of just restarting the X server, and everything works fine. I would delete the thread but idk how. :oops:

---

### Post by mahy on 2006-10-29
You have to install package linux-restricted-modules for your kernel.

---

### Post by dbott67 on 2006-10-29
I'm not sure if this works in Edgy, but it worked for me in Dapper.

[http://www.ubuntuforums.org/showthread.php?t=274915](http://www.ubuntuforums.org/showthread.php?t=274915) (ATI installation starts at step #5)

---

