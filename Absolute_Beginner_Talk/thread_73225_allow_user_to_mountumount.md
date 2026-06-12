---
title: "allow user to mount/umount"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by miodragsm on 2005-10-08
Hi! I am using ubuntu in a sort of embedded machine. It runs one program ( i wrote it ) that gathers some data from serial port. Program starts everytime machine is restarted ( i've used session startup to enable this ) and from time to time checks if usd disk is plugged in. Then it gzips data and copies it ( trough shell script ) on disk. Now, i've got this problem: when i remove the disk ( program 'beeeps' :) when he has done copying data ) sometimes there is no data on disk ( like file table is not updated or something... ). If i unmount from my program will it prevent this from happening ( when i umount manually everything is ok ) ? How can i set default user to be able to unmount ? Does USB disk gets asynchronous mode (can i set MS_SYNCHRONOUS for automount hotplug devices? and will it help? )

---

### Post by guyomarj on 2005-10-24
It's a bit late, and you have probably managed to solve your problem. But since no post should get zero replies, here is a short HOW-TO understand and edit fstab:
[How to edit and understand /etc/fstab]("http://http://www.tuxfiles.org/linuxhelp/fstab.html")

So, to allow a no-root user to mount/umount devices, you have to use the "user" option in /etc/fstab.

---

### Post by patrick295767 on 2005-10-24
[http://www.ubuntuforums.org/showthread.php?t=81368](http://www.ubuntuforums.org/showthread.php?t=81368)

---

### Post by guyomarj on 2005-10-24
[QUOTE=patrick295767][http://www.ubuntuforums.org/showthread.php?t=81368](http://www.ubuntuforums.org/showthread.php?t=81368)[/QUOTE]

:D Yes, I thought it was a goud idea to make it a HOW-TO thread. I can't remember how many times I had to Google "fstab" in my entire geek life. I'mean using an other distro than Ubuntu, of course...

---

