---
title: "Partition creating and access"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by linux_student_user on 2006-06-22
Hi I've tried this before in Ubuntu but id like to create a partition seperate of the ubuntu system, though which I can access from ubuntu as if it was a seperate drive. Basically I want a totally independent partition to store all my music and files in so if I mess something up and have to reinstall then I can still easily retrieve my data. I would be greatful for step by step instructions on creating and then accessing it. thankyou in advance :D 

Mike

---

### Post by Kobalt on 2006-06-22
You can create a brand new partition with a Live CD of Ubuntu. Put it in you drive, reboot your computer to make it start on the Live CD. Afterwards, start the Gparted tool : it will make you resize and create partitions. It's really easy, don't worry... all you have to do is resize your current partition and create a new one, with ext3 format if you use Linux only, FAT32 if you want to share it with Windows... Then you restart your computer without the Live CD, and your're done ! 

Cheers.

---

### Post by aysiu on 2006-06-22
After you create the partition, you'll probably need to add it to your /etc/fstab

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

