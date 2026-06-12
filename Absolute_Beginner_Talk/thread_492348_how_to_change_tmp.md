---
title: "how to change /tmp"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by mattze on 2007-07-04
hey,

since i m constantly running low on disk space i m looking for a way to move my /tmp directory to another partiotion. is there a way to do this?

thanks for the answers!

matthias

ps: if you have general tips on how to make ubuntu use less space i d be happy to hear them

---

### Post by Nekiruhs on 2007-07-04
You could edit your fstab ```
gksudo gedit /etc/fstab
``` look for the parition you want to make /tmp and change the folder before "ext3" to /tmp and save. ?Delete your current /tmp? and reboot.

---

### Post by davidjmayo on 2007-07-04
Before you think about moving /tmp how much space is it using ?

Do you leave your computer on all the time?? If so a restart will clear /tmp

EDIT: ooops too late

---

### Post by mattze on 2007-07-04
a simple "mount /dev/sdb2 /tmp" did it. i m a bit surprised that it is that easy but thanks a lot!

---

