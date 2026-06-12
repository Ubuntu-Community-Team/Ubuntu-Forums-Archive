---
title: "Partition Question's"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Cubedude04 on 2007-06-25
Hey, I have a few questions about partitions

A)Will i need to set my my partitions again after i upgrade to edgy then to feisty?

B)How do i rename my partitions so i know which one is Root and which one is swap and which one is Home etc?

C) I don't understand all the options e.g Primary partion (is that the main one that loads. so should that be the root or the home) and what file system do i use for the root, main and swap?

I am using Dapper Drake if that helps on a live cd and going to install 

Thanks in advance :)

---

### Post by vanadium on 2007-06-25
A) Short and long answer: no

B) The partition names are only used by the system administrator. Once the administrator has them mounted, you access them through the regular file system. Thus, there is no practical use of being able to rename them. Your partitions have names such as hda1, hda2, or sda1, sda2, or sdb1, 2, etc, i.e., the name of your hard drive (hda, hdb, sda, sdb, ..) and a number. The system admin decides where these are mounted.

C) My advise is that you leave partitions allone until you have a good understanding of what they are and how they work. If you are installing a new system, just have the installation program do the partitioning. By default, Ubuntu will create one root partition and one appropriately sized swap partition and that is perfectly fine for an end-user desktop system.

---

