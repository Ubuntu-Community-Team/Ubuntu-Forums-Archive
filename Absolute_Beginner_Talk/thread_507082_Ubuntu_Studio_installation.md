---
title: "Ubuntu Studio installation"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Hellpig on 2007-07-22
Short and sweet version:

I used Partition Magic to create a Linux Ext3 partition (running Windows from start). Ubuntu discovers the partition but it only says somthing like "unable to write changes to disk, missing root/file system". My Linux knowledge is not so good... anyone who can gimme a pointer here? :)

---

### Post by testube_babies on 2007-07-22
In the Installer's built-in partitioner, make sure to set the ext3 partition's mount point to root (/).

---

### Post by steve.horsley on 2007-07-22
I advise that you delete those partitions again and leave the disk sapce unallocated. Then use the Linux installer and take the option to use the free disk space. This bpasses having to explain to the installer that you want it to use **that** partition as root and **that** one as swap. It also bypasses the fact that Linux often seems to have difficulties with ext3 partitions created by Partition Magic.

---

