---
title: "Problem Partioning and Instaling Ubuntu 7.04"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by barney6221 on 2007-08-28
I am having a problem partitioning the 60 GB hard drive on my HP Laptop computer.  I initially want to have a dual boot system.

I defragmented the hard drive but did not delete the swap file.  I booted up with Ubuntu Linux 7.04 CD and attempted to partition the hard drive using the software on the CD.  I selected approximately 15 GB for this partition and started the procedure.  I got an error message and a partition of 8 MB.

I have since tried to delete this partition without success.  In the meantime I deleted the swap file and
defragmented the hard drive 6 to 8 times before proceeding with the following steps.

I downloaded the gparted 0.3.4-8 iso file (Linux partition software) and burned the image to a CD.  I booted with this CD and still was unable to delete the 8MB partition or to prepare a partition of adequate size to install this version of Ubuntu Linux.

When I select the 8MB partition with gparted program the delete button is disabled.  If I select the 1st partition and try to resize it to give me a partition of adequate size the program refuses to allow me to drag the bar to the left to make another partition.

What do I need to do to delete the 8MB partition that was initially created with the Ubuntu 7.04 installation disk and restart the process?

The laptop is a pentium.  Is the laptop the problem? 

I would appreciate any help with this problem.  Thank you.

---

### Post by Inxsible on 2007-08-28
[Partitioning]("http://www.psychocats.net/ubuntu/partitioning")

[Installing]("http://www.psychocats.net/ubuntu/installing")

Check those two links. They have good info on partitioning and installing Ubuntu. Also remember that if the partition is mounted, you cannot delete it or make any changes to the file system on it. So unmount the partition before you try to delete it.

---

### Post by shinjiKobiyashi on 2007-09-10
i just got a new computer yesterday and it currently has widows XP and has many viruses and when i try to boot from my linux ubuntu 7.04m copy it goes to this screan that has like master and slave and usb prot stuff and at the bottom it has initalizing pool data....... then it says boot from CD with this :_ and the under-scroe is blinking like to type something in but i have tried yes and enter but the keyboard is not responding but the keyboard is working and this moarning i wated for about 30-45 minutes and it went to like start windows normaly and safe mode but safe mode would not work but it will let me run window but slowly i think i may be able to format my computer if you have any pointers or ideas please help me thanks

---

### Post by dptxp on 2007-09-10
> **barney6221 said:**
> I am having a problem partitioning the 60 GB hard drive on my HP Laptop computer.  I initially want to have a dual boot system.

I defragmented the hard drive but did not delete the swap file.  I booted up with Ubuntu Linux 7.04 CD and attempted to partition the hard drive using the software on the CD.  I selected approximately 15 GB for this partition and started the procedure.  I got an error message and a partition of 8 MB.

I have since tried to delete this partition without success.  In the meantime I deleted the swap file and
defragmented the hard drive 6 to 8 times before proceeding with the following steps.

I downloaded the gparted 0.3.4-8 iso file (Linux partition software) and burned the image to a CD.  I booted with this CD and still was unable to delete the 8MB partition or to prepare a partition of adequate size to install this version of Ubuntu Linux.

When I select the 8MB partition with gparted program the delete button is disabled.  If I select the 1st partition and try to resize it to give me a partition of adequate size the program refuses to allow me to drag the bar to the left to make another partition.

What do I need to do to delete the 8MB partition that was initially created with the Ubuntu 7.04 installation disk and restart the process?

The laptop is a pentium.  Is the laptop the problem? 

I would appreciate any help with this problem.  Thank you.

On partitions-
First delete all partitions except the 1st one for windows.
Then resize (make sure that round to cylinders is ticked) to make other partitions.
8 MB is a very small space to lose, but yes it is irritating.

---

