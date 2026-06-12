---
title: "installing ubuntu linux on partitioned drive"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by chrissev on 2006-07-31
anyone know if it's possible to install linux ubuntu on one side of a partitioned drive, and have windows on the other side?  I have a partitioned drive with one half completely empty and the other half with windows and associated programs, and would like to put ubuntu linux on the empty side.

---

### Post by bruenig on 2006-07-31
It is possible. With the empty half you are going to want to create an extra partition that is twice the size of your RAM and make that your swap partition. With the remaining space of the empty partition, you can put your root ubuntu installation. The install automatically installs grub and allows you to choose which OS to boot into everytime you start your computer.

---

### Post by djsroknrol on 2006-07-31
hi chrissev..

go **[here]("http://ubuntu.mirrors.tds.net/pub/linux/ftp.ubuntu.com/releases/5.10/")**

get your install iso burned and make sure your BIOS is set to boot from the CD-ROM, and the rest is all good...the partitioner will allow you to use the unused space to install Ubuntu...good luck and welcome aboard...

---

### Post by chrissev on 2006-07-31
one more question:  I'm planning on installing ubuntu linux on a partitioned (FAT32) acer laptop (travelmate 2300).  Can I do this, or are laptops un-ubuntu-able?  I have an ubuntu 6.06 LTS CD that was mailed to me and I'm all ready to go, just making sure nothing is going to go wrong before I start.

---

### Post by djsroknrol on 2006-07-31
Is the whole disk fat 32?. If it is, it needs to be resized with something like GParted..the partition needs to be shrunk down to make room for the install. How big is the disk?...you need to make a minimum of 8 - 10GB of space for a nice install.don't know about any issues with the travelmate, but you can search for it.

---

