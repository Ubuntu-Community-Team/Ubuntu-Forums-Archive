---
title: "allow user to mount/umount"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by miodragsm on 2005-10-08
Hi! I am using ubuntu in a sort of embedded machine. It runs one program ( i wrote it ) that gathers some data from serial port. Program starts everytime machine is restarted ( i've used session startup to enable this ) and from time to time checks if usd disk is plugged in. Then it gzips data and copies it ( trough shell script ) on disk. Now, i've got this problem: when i remove the disk ( program 'beeeps' :) when he has done copying data ) sometimes there is no data on disk ( like file table is not updated or something... ). If i unmount from my program will it prevent this from happening ( when i umount manually everything is ok ) ? How can i set default user to be able to unmount ? Does USB disk gets asynchronous mode (can i set MS_SYNCHRONOUS for automount hotplug devices? and will it help? )

---

