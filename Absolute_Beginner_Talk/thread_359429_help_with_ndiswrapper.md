---
title: "help with ndiswrapper"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by coincutter on 2007-02-12
error make sure you are running as root - did cd / 
trying to install driver for net gear wireless and cant get proggy to create a directory

maybe i shold give up on this and hardwire?

---

### Post by vigleik on 2007-02-12
Just so we're clear. To execute a command as root you type "sudo command". As in "sudo ndiswrapper -i mydriver.inf" or whatever it is. "cd /" puts you at the base of the filesystem, and has nothing to do with running as root. Or maybe I'm misunderstanding.

---

### Post by aysiu on 2007-02-12
Try this: ```
sudo apt-cdrom add
``` Then insert the Ubuntu CD when prompted ```
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

