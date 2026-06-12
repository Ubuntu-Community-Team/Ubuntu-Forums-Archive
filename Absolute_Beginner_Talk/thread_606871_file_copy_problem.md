---
title: "file copy problem"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by syerkb on 2007-11-08
i need to copy the contents of a folder to another directory.  i have created the target directory, however the owner is root and will not allow any modification.  how can i copy these files?

the file is: /home/public/test  and the target is: /usr/local/src/alsa

please help!

---

### Post by Maestro23 on 2007-11-08
> **syerkb said:**
> i need to copy the contents of a folder to another directory.  i have created the target directory, however the owner is root and will not allow any modification.  how can i copy these files?

the file is: /home/public/test  and the target is: /usr/local/src/alsa

please help!

**/usr** is owned by **root**. You need to preface you copy command with **sudo**.

sudo cp .....

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by syerkb on 2007-11-08
i have prefaced cp with sudo but then i get the message: no such file or directory.

i tried:  sudo cp -i /home/public/test /usr/local/src/alsa

---

