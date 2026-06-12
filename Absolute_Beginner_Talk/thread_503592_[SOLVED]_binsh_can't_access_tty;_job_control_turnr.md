---
title: "[SOLVED] /bin/sh: can't access tty; job control turnrd off"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by cancaseiro on 2007-07-18
Hi! I have problem. I can't log into my Ubuntu Feisty Fawn Linux server version. It loads till the message that is the name of this thread and then stops. I have tried adding ramdisk=8192 to my lilo.conf but it didn't help. I put up my lilo.conf file here so everyone can see what it looks like and maybe give some tips what to do to get rid of this error as fast as possible as it is very important server for my work place and we need to get it up and running as fast as possible. I needed to install Lilo because I wanted to make Mac OS X Intel server to boot straight into Linux not Mac OS X.

Lilo conf:

```
boot=/dev/sda3
default=Ubuntu

map=/boot/map
delay=20
image=/vmlinuz initrd=/initrd.img
root=/dev/sda3
append=noapic
label=Ubuntu
read-only
```

For me everything seems to be right as it should boot into sda3 drive and default is Ubuntu as well.:confused:

---

### Post by cancaseiro on 2007-07-18
My fdisk -l:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2   *          26        5248    41943040   af  Unknown
/dev/sda3            5264       30402   201919632   83  Linux
/dev/sda4            5248        5264      131072   82  Linux swap / Solaris

Partition table entries are not in disk order
```

I thought that fdisk -l might be usefull too to put up here sda3 is the partition where my Ubuntu is.

---

### Post by cancaseiro on 2007-07-18
Please somebody help me! :(:-k

---

### Post by cwmoser on 2007-07-18
I've got a PC that acting the same way -- during installation the following error is displayed:

BusyBox v1.1.3 (Debian 1:1.3.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh:  can't access tty; job control turned off
(initramfs)


This PC is a 1.7Ghz PC with IDE CDROM and Hard Drive.

The same error occurs with the Live CD , Alternate CD,  Ultimate CD, and also with Ubuntu Server CD.

Carl

---

### Post by wpshooter on 2007-07-18
> **cancaseiro said:**
> Please somebody help me! :(:-k

Dear Cancaseiro:

If you do some research on this forum regarding this error, I believe the conclusion that you will come to is that NO ONE yet seems to know exactly what is causing this error.  

And I find it hard to believe that after all this time that the developers of Ubuntu are not aware to this problem.  My GUESS is that as long as this error has been occuring, is that they have not fixed it because they can not figure out what is causing it.

Good luck to us !!!

---

### Post by cancaseiro on 2007-07-18
Ok! That's bad. I thought maybe someonehas found sometihing as I didn't find solution from previous posts in this forum but if You say that the problem is still unsolved then I think I should uninstall Lilo somehow. Does anyone know good method to uninstall Lilo with the help of live Linux cd? I tried ```
/mnt/sbin/lilo -u
``` but it said ```
root@ubuntu:/mnt# /mnt/sbin/lilo -u
/mnt/sbin/lilo.real: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /mnt/sbin/lilo.real)
``` mnt is there because that's where I mounted my Linux partition.

---

### Post by fluteflute on 2007-07-18
For me I got it to work by placing a floppy disk with write protection (flick the switch thing) in the drive.

---

### Post by cancaseiro on 2007-07-19
I can't use any floppies and I would like to uninstall it so if someone knows how to do it without harming the Linux itself then I would like to know it too. Meanwhile I will Google on it by myself and check in from time to time.

---

### Post by cancaseiro on 2007-07-19
Anybody? :confused:](*,)

---

### Post by cancaseiro on 2007-07-20
Ok, I just installed Grub over Lilo and now the system works only bad thing is that Mac OS X is first boot device but I can live with that.

---

