---
title: "Install Ubuntu as a Dual Boot on a slave drive"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by nathan42100 on 2008-02-05
My situation is slightly "unique". Because I don't want to give up windows just yet (+I don't use linux so I would like to learn first), I would like to install Ubuntu. My master drive does not have enough space on it to warrant an ubuntu installation, but my slave has over 150 GB free. I would like to repartition the slave so ~80 gigs can be used for ubuntu without loosing the ~80 gigs of info currently on there. In an older version (8.0) of PartitionMagic it says that if I just shrink the partition from the back-end forward, then the partition will not be bootable, however I don't really want to move everything on that partition backward because a) it will take time and b) more possibility of data corruption(?). If I choose to install GRUB (from what I can tell its what I am supposed to do for my situation) on my Master (i have a few gigs) so that it see Windows and stuff as my primary, will it boot ubuntu from the slave even though it isn't "bootable"? Can the ubuntu install be installed to the slave (currently on cable select, not jumpers and I don't want to open my case...) at all? Can the ubuntu install resize the drive for me? 

Can someone guide me through the install?

---

### Post by wolfen69 on 2008-02-05
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by nathan42100 on 2008-02-05
I know all that...is there an equivalent for option A in the partitioning on a slave drive? Or should I choose Option C...I want to save all the stuff on my drives so option B is out of the question. The problem with C is that I don't know what I am doing...will it show hdb for the slave drive?

---

### Post by wolfen69 on 2008-02-05
just download the gparted live cd to resize your drive. you should have no problems.

---

### Post by nathan42100 on 2008-02-05
not that I don't trust you, I am just a little paranoid here. Can someone else confirm that this will work just fine? Then after that how do I select in the Ubuntu installer to install to the unallocated space on the slave?

---

### Post by nathan42100 on 2008-02-05
Should I create a primary or a logical partition to install ubuntu on to?

---

### Post by ajgreeny on 2008-02-05
I don't think it matters where on the slave drive you put ubuntu, it will still be recognised and bootable using grub, whether grub is on the master or the slave drive.  Normally the ubuntu installer will put grub on to the first drive and will replace the windows MBR.  Although this may seem worrying, don't let it stop you; even if things did go wrong it easy to restore the windows MBR if you really have to using the windows install CD.
So simply use the ubuntu live CD partition editor to reduce the size of your slave drive partition and leave 80GB unallocated, then install ubuntu to that unallocated space, by choosing Manual at the partitioning stage of the install, and making a 79 GB ext3 partition for / and a 1 GB partition for swap, (the exact sizes may be slightly different to those but will be around that in most installs on a total of 80GB).  It will not matter really whetherv you make a primary or extended partition as long as you are not trying to make more than 4 primary partitions on the disk.  Most swap partitions are extended if you let ubuntu do the default install on a total drive so you could certainly do that if numbers are too high to use primary for both ubuntu partitions.
It may all sound frightening, but it isn't really so bad.

---

### Post by nathan42100 on 2008-02-05
2 questions
1) what is swap exactly. ive heard of it but don't really know what it is...
2) The cd partitioning editor would be option C? or A? Can you choose the slave drive in option A?

---

### Post by nathan42100 on 2008-02-05
ajgreeny, do you have aim so I can talk with you (on my laptop) during the install at around 9pm EST?

---

