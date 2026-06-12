---
title: "Installing from CD / partitioning"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by usr0815 on 2006-08-15
Hi,

I've installed Breezy Badger previously on a Dell Inspiron 6400 and had no problems. I am now trying to install Dapper Drake on a Dell Inspiron E1705 and have some major teething trouble.

1. I downloaded the ISO file and then burnt it to a CD as an image. However when I restart the computer with the CD and choose to boot from the CD it tells me it is not bootable. I can see the individual files on the CD, and don't know if it is an ISO image burning problem. (I used the freeware [ISO Recorder]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm")). Any suggestions?

2. With my Badger install, I first partitioned the disks and then installed Badger. I am assuming I can simply install from the Dapper CD and choose to partition as part of the install process.

I want to preserve my Windows XP installation - could someone please advise me on what is likely to show up and what I should choose  to partition? If I choose to install to the existing Windows NTFS partition I suppose I should get an option that resizes it without deleting anything. Does this make sense?

Thanks very much.

---

### Post by siacs on 2006-08-15
You can check the iso by using the md5 checksum. The md5sums for the image will be on the site you downloaded from. For example
[http://ubuntu-releases.cs.umn.edu//kubuntu/6.06/MD5SUMS](http://ubuntu-releases.cs.umn.edu//kubuntu/6.06/MD5SUMS)  For Windows there are freeware md5 checkers available. 

The way you partitioned before with Breezy is preferable. But yes you can use GParted during the installation to resize.

Information on partitioning
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

What it shows up like
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by usr0815 on 2006-08-15
siacs, Thanks so much for the pointers and answering all my questions.

---

### Post by siacs on 2006-08-16
You're welcome, happy to have helped :)

---

