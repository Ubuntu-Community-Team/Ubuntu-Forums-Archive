---
title: "[SOLVED] Grub Error 15 about 35% of the time"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by icceric on 2008-01-26
I know that it means the partitions are all ok, but it can't find the required files to boot.  But I only get this error on once out of maybe three boots... I restart and it's fine.  This started happening after I moved the computer from one room to another yesterday (and I have booted for one reason or another several times since), it's strange. A few times I opened the computer and checked that everything was plugged in tightly etc.  Would there be any other reason this would happen?

Thanks in advance!

Regards,
Eric

---

### Post by dstew on 2008-01-26
That is a "File not found" error. Since it is intermittent, it may be a hardware or disk error, perhaps a problem reading the file system table.

The most common hardware problem is with an IDE ribbon cable (if that is the type of drive you have). Get another ribbon cable and use it, and see if the errors go away.

The disk errors can be looked at and sometimes fixed with the **e2fsck** program. I suggest running a file-system check on the hard disk linux partition. To do this, you should boot a Live CD, so you can run the check on the hard disk when it is unmounted. From the Live CD terminal command line, enter the command```
sudo fdisk -l
```Find the partition that has your Linux system on it, and use that partition name in the command. For example, if your linux partition is /dev/sda1, the command would be```
sudo e2fsck /dev/sda1 -vp
```Some the -v option causes it to be verbose, that is, tell you everything it is doing, and the -p option causes it to fix any errors it finds without asking you.

One caution: it is possible that during the attempted fix files may be lost. I have not had this problem, but sometimes, especially if the disk is dodgy, you can lose things. If you have any precious files on that partition, and you can get it booted, make a back-up before trying the repair.

---

### Post by icceric on 2008-01-26
Thank you for the very detailed answer!  There's nothing real important on there, but it is an ide cable.. one of those non-ribboned wrapped up into a cable ones.  I will check it out asap.

Again, thanks for the fine detail.

Regards,
Eric

---

### Post by icceric on 2008-01-27
I changed the IDE cable last night and so far so good... rebooted several times.  If that error comes up again I will check out e2fsck.  Thanks much!

---

