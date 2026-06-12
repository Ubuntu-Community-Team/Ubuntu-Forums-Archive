---
title: "system restore?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-12-13
Is there a system restore for ubuntu?(like the 1 in windows)

---

### Post by xyz on 2006-12-13
Not in the Windows sense...

Originally posted by Heiode/A-Star:

In a terminal, type and wait til it's finished:
```
sudo su
cd /
 tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/sys /

Restore command:

tar xvpzf backup.tgz -C /

Just hit enter/return/your brother/whatever and watch the fireworks. Again, this might take a while. When it is done, you have a fully restored Ubuntu system! Just make sure that, before you do anything else, you re-create the directories you excluded:
Code:

mkdir proc mkdir lost+found mkdir mnt mkdir sys etc...

And when you reboot, everything should be the way it was when you made the backup!

```

There are other ways : search a bit for backup/restore using Partimage, Live CD, rsync...

---

