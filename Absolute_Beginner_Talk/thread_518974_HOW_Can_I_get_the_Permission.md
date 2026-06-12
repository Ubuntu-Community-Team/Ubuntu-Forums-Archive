---
title: "HOW Can I get the Permission?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by ela04cz on 2007-08-06
I changed 5 system files to speedup the xubuntu 7.04 booting process, but I screwed up. They are 

etc/modprobe.d/aliases
etc/init.d/rc
etc/hosts
etc/sysctl.conf
/boot/grub/menu.lst

Now I cannot start the X desktop, under the recovery mode, I found  root(none): instead of root(ela04cz) which is the case when things were right.

I tried to modify those files back, but "permission denied" and "Read-only file" hold me back. Can someone  tell me how to get the permission please? By the way, I know how to use sudo, I tried sudo nano /etc/init.d/rc, I can access the file and cannot change it.

Pre-thanks to everyone who read through this.

---

### Post by nichipet on 2007-08-06
Try

```
ls -l /etc/modprobe.d/aliases
ls -l /etc/init.d/rc
ls -l /etc/hosts
ls -l /etc/sysctl.conf
ls -l /boot/grub/menu.lst
```

And give the output here. It sounds like write permission is missing, which is an easy fix, but we should see the output first to be sure.

---

### Post by Wim Sturkenboom on 2007-08-06
I assumed that you changed the permissions, although not that sure anymore. Anyway, to change permissions the command you're looking for is *chmod* (in combination with sudo)

i.e. *sudo chmod 421 yourfile* makes yourfile only readable by the owner, writable by the group and excutable for others; *sudo chmod 700 yourfile* makes it readable (4), writable (2) and executable (1) by the owner and (nothing fro the group and others, 

On my dapper system, the permissions are 644, 755, 644, 644 and 644 (in sequence of the files that you gave).

---

### Post by asmoore82 on 2007-08-06
use the LiveCD to fix it.

---

### Post by ela04cz on 2007-08-06
Guys, thanks for your suggestions, I download a script and now can see the ubuntu file system from XP. But after I change everything back, it still says /etc/init.d/rc not found, why is that? I mean, I can see this file within windows, but ubuntu cannot find it?

---

### Post by aysiu on 2007-08-06
If you're in recovery mode, you should have access to all files. Recovery mode logs you in as the root (administrator) user.

---

### Post by ela04cz on 2007-08-06
yes, the thing is, now I don't have the permission even in recovery mode! The prompting line use to be root@ela04cz~: in recovery mode, but now it is root@(none)!

Anyway, I have the access to the system files from XP now, but even after I changed all this back (I suppose I changed everything has been fixed back to what they were) I still have these:
-bash: /dev/null  Permission denied
/etc/init.d/rc not found
etc/init.d/rsS Permission denied
rcS-sulogin main process killed by TERM...

---

### Post by aysiu on 2007-08-06
It seems as if something has gone terribly wrong. Perhaps your /etc/fstab file is invalid, or your /etc/hosts file doesn't contain the name of your computer.

If you're going to make repairs, you'd have to use the Desktop CD as a live CD. Otherwise, a reinstall may be the quickest way to fix this.

---

### Post by ela04cz on 2007-08-06
Hi Nichipet, thanks a lot for your help
I entered this:
```
ls -l /etc/modprobe.d/aliases
ls -l /etc/init.d/rc
ls -l /etc/hosts
ls -l /etc/sysctl.conf
ls -l /boot/grub/menu.lst
```

And these are the output:
> -rw-r--r-- 1 root root 4549 Aug 6 04:49 /etc/modprobe.d/aliases
-rwxr-xr-x 1 root root 8530 Aug 6 04:20 /etc/init.d/rc


The  init.d/rc file name is highlighted with green colour, and also I noticed the front part is different from all the others (the other three are the same with the modprobe.d.

Can u tell me how to change this back?

---

### Post by annda on 2007-08-06
ela, your permissions are OK. the problem must be somewhere else...

maybe check aysiu's advice on the hosts file.

---

