---
title: "Data Loss on shared Volume ubuntu/win8"
date: 2013-09-27
forum: Any Other OS
---

### Post by stefanpiat on 2013-09-27
Hello,

I am using ubuntu 12.04 together with windows 8 on the same computer,

ubuntu is installed on a ssd harddrive, and windows 8 on a IDE  harddrive, on this hardrive I have also a fat32 partition I am using to  share files between ubuntu and windows.

my problem is that when I do copy files from ubuntu to this fat32 partition, I lost them after reboot, shutdown.
even if I unmount my volume before doing so.
I am not sure this has always happens...
I have not test all the different combination (of rebooting and switching OS)

windows can recover the lost files after a disk repair, I can also recover them with photorec (for instance)

do you have any help, knowledge hon how to fix this?

best,
stéfan piat

---

### Post by westie457 on 2013-09-27
Have you disabled Windows Fastboot and other versions of sleep/hibernation?
If you have not then Windows will ignore any changes to the master file table.

Windows must be completely shutdown to allow the partitions to be unmounted and to allow files to be written to them from Linux OS's.

For preference on my system the data partition is formatted to NTFS, the file-system type should not really make a difference

---

### Post by stefanpiat on 2013-09-27
wow thanks, that was it.

---

