---
title: "How to view Partitions?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by oxsyn on 2008-01-20
I've got a secondary 500GB NTFS drive on my Gutsy Desktop.  Typically, I mount this by going to Places -> Computer ->  Storage Drive and then I see a prompt for my root password to mount the drive.

I'd rather have it automounted when I boot the machine.

I found this tutorial: [http://www.goitexpert.com/entry.cfm?entry=Automount-NTFS-Drive-in-UBUNTU](http://www.goitexpert.com/entry.cfm?entry=Automount-NTFS-Drive-in-UBUNTU)

Which says I should edit my /etc/fstab and add a line similar to: 

/dev/sda1 /mnt/sda1 ntfs users,defaults,umask=000 0 0

However, I need to know the partition name (is that the correct terminology?) for my drive.  I'm referring to the /dev/sda1 portion.  How do I find that information, and what is it called?

---

### Post by smartboyathome on 2008-01-20
Install gparted, either from the repo or from getdeb.net, and look for the partition in there.

---

### Post by thelatinist on 2008-01-20
```
sudo fdisk -l
```

Will list all of the partitions on all your hard drives.

---

### Post by FurryNemesis on 2008-01-20
running 

blkid 

in the terminal will give you the UUIDs and the partition names of all mounted disks. Not sure if it works with NTFS though.

---

### Post by oxsyn on 2008-01-20
Thanks, worked perfect!

---

### Post by oxsyn on 2008-01-20
> **thelatinist said:**
> ```
sudo fdisk -l
```

Will list all of the partitions on all your hard drives.
OH!  I tried just fdisk -l and it didn't work.  Apparently the you need root privileges.

---

### Post by thelatinist on 2008-01-20
> **F4RR4R said:**
> OH!  I tried just fdisk -l and it didn't work.  Apparently the you need root privileges.

Some people claim it does not need root privileges just to run the -l switch, but I have never gotten any results from fdisk -l without them. *shrug*

---

