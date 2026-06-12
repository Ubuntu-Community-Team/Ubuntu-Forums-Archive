---
title: "Installing Ubuntu on VPC"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by chr1zis on 2007-10-24
Hello all. I am going to install Ubuntu on my Averatec laptop using VPC 2007 but I had a quick question. I have only a single drive on my laptop ('C:') and therefore would like to create a partition. What type of partition do I need to create in order to create a new VPC? Would I need to create a logical partition or a primary partition? Thanks in advance.

---

### Post by bsharp on 2007-10-24
If you are running Ubuntu in a virtual machine then you don't need to make a partition, I haven't used VPC in a looong time but I think you just need to make a new virtual hard disk.

---

### Post by chr1zis on 2007-10-24
Thanks for the quick reply. Do you have any idea how to make the new virtual disk?

---

### Post by chr1zis on 2007-10-24
Also, if I am going to use a virtual disk... would that disk need to be on a disk other than 'C:'? or do you think that will work okay?

---

### Post by bsharp on 2007-10-24
I think to make a new virtual disk you just go to File>New Virtual Disk or something.

A virtual disk is just a file on your hard drive that VPC treats as an actual hard disk, so it will be fine on C:

---

