---
title: "How to use external hard disk with USB connection?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by paker on 2008-04-03
An old IDE 30GB hard disk is connected via USB, automatically mounted as "lost + found." I cannot write to it. I cannot format it. I can do nothing with it. Please help. Thanks.

---

### Post by jakupl on 2008-04-04
I actually have the same problem... although I think my hard disc is broken

---

### Post by superprash2003 on 2008-04-04
which filesystem?

---

### Post by jakupl on 2008-04-04
I dont understand the question :confused::popcorn:

---

### Post by kpkeerthi on 2008-04-04
If you are looking to recover data from corrupted disks [test disk]("http://www.cgsecurity.org/wiki/TestDisk") may help. Test Disk is bundled with [system rescue cd]("http://www.sysresccd.org/Main_Page")

[More Info]("http://www.cgsecurity.org/wiki/TestDisk_6.9_Release")

---

### Post by jakupl on 2008-04-04
can you use it with an external hard disk with usb connection?

---

### Post by brian_p on 2008-04-04
> **paker said:**
> An old IDE 30GB hard disk is connected via USB, automatically mounted as "lost + found." I cannot write to it. I cannot format it. I can do nothing with it. Please help. Thanks.

Removable disks are usually mounted on a directory in /media. Not that that necessarily accounts for your problem.

Find the device name. It will be something like /dev/sdx. If it's mounted the command 'mount' in a terminal will tell you.

Unmount and see how you go on with 'fdisk /dev/sdx' or 'cfdisk /dev/sdx'.

---

### Post by kpkeerthi on 2008-04-04
Yes. Just follow the instructions from test disk web site.

---

