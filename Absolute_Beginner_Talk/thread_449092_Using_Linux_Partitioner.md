---
title: "Using Linux Partitioner"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-05-19
I'm following the graphical install but the partitioner is different in my 7.04 Feisty Fawn then that of the graphical install walkthrough.  I'm making it dual boot so i chose to prepare disk space manually.  Now to create 2 partitions, /home, /swap... how do i do this?  take my hard drive partiton say 40GB then partition that 40 again to 38GB and 2GB? i tried doing this but as soon as i amde the second partition the 38GB was deemed unusable!

Any help would be greatly appreciated

Thanks, Alain

---

### Post by bobplano on 2007-05-19
you need a /(root) partition too. it should be 5-10gigs depending on how much software you are going to install. what do you mean the 38gig partition was deemed unusable?

---

### Post by S15_88 on 2007-05-19
ok bear with me here, this is what i've got : 

Device         Type    Moutn Point    Size                    Used
/dev/sda
   /dev/sda1 Fat16  /media/sda1    49         MB         33  MB
   /dev/sda2 ntfs     /media/sda2    10737   MB     4500  MB
   /dev/sda3 ntfs     /media/sda3    149251 MB    18300 MB

I Edit /dev/sda3 and creat 40GB of free space,  Take the free space and create a new partition size 38GB: Primary, location: begining, use as: ext3 mount point: /home

Then Under device it says Unusable 1998 MB! but that's the stuff i want for the /swap.

so how many partitions to a make? /home  35GB? , /root 10GB? , /swap 2GB?  And how do i create all these!?!?!

Thanks for the ongoing help and support, Alain

---

### Post by Bachstelze on 2007-05-19
You can have no more than four primary partitions on a hard drive. If you want more than four partitions, you'll have to create an Extended partition and then create Logical partitions in it.

---

### Post by S15_88 on 2007-05-19
ic ic ok i'll mess around with it we'll see how it goes!

---

### Post by S15_88 on 2007-05-19
I have all my partitions set up like so:

Device        Type   Mount Point   Size              Used
/dev/sda
/dev/sda1   Fat16  /media/sda1         49  MB        33 MB
/dev/sda2   ntfs     /media/sda2   10737  MB    4500 MB
/dev/sda3   ntfs     /media/sda3  149251 MB  18300 MB
/dev/sda5   ext3   /home               34998 MB  Unknown
/dev/sda6   ext3   /root                 10001 MB  Unknown
/dev/sda7   ext3   /swap                 1998 MB  Unknown

I click Forward and get this:  No root file system is defined. Please correct this from the partitioning menu.

Whats the deal??

Thanks, Alain

---

### Post by Bachstelze on 2007-05-19
The "root filesystem" is / - it is *not* the same as /root !

---

### Post by S15_88 on 2007-05-19
should the root, "/", be the largest partition?

---

### Post by H.E. Pennypacker on 2007-05-19
The following pages may prove helpful:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Malibu Illusion on 2007-05-19
Your /home partition should be your largest.  /swap should be around 2 GB.  Rest in /.

Take care.

---

### Post by S15_88 on 2007-05-19
thanks, that what i've got now but when i hit forward it says i need a partition for the swap, how come the current one i have there isn't being recognized?

---

### Post by Bachstelze on 2007-05-19
You have a slight confusion here. You made an ext3 partition, mounted on the /swap directory. A swap partition is not that at all, it uses it's own filesystem and is the Linux equivalent of Windows' virtual memory. When making your swap partition, you mush choose the filesystem linux-swap.

---

### Post by S15_88 on 2007-05-19
ya i kinda missed that part haha my bad! i've got it goin now

Thanks, Alain

---

