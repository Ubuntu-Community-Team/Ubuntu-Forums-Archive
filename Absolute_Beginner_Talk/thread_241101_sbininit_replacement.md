---
title: "/sbin/init replacement?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Emceay on 2006-08-21
When I try to start ubuntu, it says it can't find /sbin/init and hangs. Is there any way to overwrite /sbin/init without destroying data? Or somehow force ubuntu to find /sbin/init?

I used Grub's command line and tried find /sbin/init and it returns Error 15: File not found

fstab says:
> /dev/sdb1    /    ext3  defaults,errors=remount-ro  0 1

/dev/sdb, according to cat /boot/grub/device.map is located on hd2, which is strange, because ubuntu won't boot (and eventually fail) unless I set it's drive to hd1.

Beyond those commands, i've hit a wall as to what to do to get my ubuntu back. Does anyone know what I can do to get /sbin/init to work? Trying to fix it has fragged two days so far.

---

### Post by Emceay on 2006-08-21
> Uncompressing Linux... Ok, booting the kernel.
mount: Mounting /dev/sdb1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

That's what the most recent attempt to start ubuntu returned. This is starting to look hopeless.

---

### Post by Emceay on 2006-08-21
After loads of link hopping, the magic words were found here: [http://www.ubuntuforums.org/showthread.php?t=172167](http://www.ubuntuforums.org/showthread.php?t=172167)

Last post:
> Never mind. A quick 'e2fsck /dev/Ubuntu/root' fixed it.

I wish I knew about e2fsck 4 hours ago

Maybe this can save someone 4 hours in the future.

---

