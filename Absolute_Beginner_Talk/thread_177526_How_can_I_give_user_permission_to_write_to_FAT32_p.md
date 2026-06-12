---
title: "How can I give user permission to write to FAT32 partition?"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by KillrBuckeye on 2006-05-16
Hello, I am a Linux noob, and I'm wondering how I can set up my FAT32 partition to allow me to write/modify files on it without having to login as root or use the sudo command every time!  The partition is mounted at "/media/DB_Storage" (DB_Storage = dual boot storage... creative, eh?).  I have tried a "sudo chmod 777 * " from within this directory as well as a "sudo chmod 777 /media/DB_Storage" and neither seems to give my user account write permission.  I have also tried:

"sudo chown chris:chris /media/DB_Storage"

This gives me some error like "The operation could not be completed" or something along those lines.  What am I missing here?

---

### Post by Jagot on 2006-05-16
Use this guide:

[http://help.ubuntu.com/starterguide/C/ch05.html#id2532903](http://help.ubuntu.com/starterguide/C/ch05.html#id2532903)

---

### Post by KillrBuckeye on 2006-05-16
Ah fstab, of course!  How could I forget that?  Thanks!

---

