---
title: "Backup for a Clean Install"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by natibo on 2008-04-18
As a noob I have been playing around quite a bit with Ubuntu.  Found programs I liked, did not like, etc.

At some point I would like to do a clean install.  The simple backup program includes the following files:

/var/
/usr/local
/home/
/etc/

It excludes:

/media/
/var/cache/
/var/spool/
/var/temp/

Does this sound right?  I know I want to backup my home directory.  I just don't know what all of the other stuff is.

---

### Post by sanus|art on 2008-04-18
From noob to noob, I'll advice you to make some sort of launcher for this backup purpose only.

Here is mine as an example: 
```

sudo tar cvpzf /media/XP/ubuntu_backup.tgz --exclude=/proc --exclude=/media --exclude=/cdrom --exclude=/lost+found --exclude=/ubuntu_backup.tgz --exclude=/tmp --exclude=/mnt --exclude=/sys /

```

---

### Post by Tews on 2008-04-19
Get Quick-Start!  Quick was developed specifically for your situation.  It is the closest thing to System Restore you will find.

[IMG]http://www.libertymanor.org/menu.png[/IMG] 

You can get it here ==> [http://http://ubuntuforums.org/showthread.php?t=613462]("http://http://ubuntuforums.org/showthread.php?t=613462")

---

