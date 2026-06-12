---
title: "help please hard drive detection"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by unshaven123 on 2006-12-14
I have installed ubuntu 6.10 it has detected everything except the spare hard drive and the other partitions [windows] on the hard drive that it is installed on

---

### Post by bulldog on 2006-12-14
Thanks sharing with us. :D

---

### Post by taurus on 2006-12-14
> **unshaven123 said:**
> I have installed ubuntu 6.10 it has detected everything except the spare hard drive and the other partitions [windows] on the hard drive that it is installed on

Is there a question somewhere in there?

---

### Post by unshaven123 on 2006-12-14
when i installed ubunto once before it detected my other drives and partitions and allowed me to access them this time did not happen and if i am to migrate to ubunto need  access to all my hard drives

---

### Post by taurus on 2006-12-14
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, paste the following output here!

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by jeremy on 2006-12-14
If you would like help on how to automatically mount the partitions and 2nd HD, have a look at:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by unshaven123 on 2006-12-14
sorry to be a pain but followed the how 2 at psychocats.net and have come across a problem
this is different from shown on the website and don't know what to do

GNU nano 1.3.12             File: /etc/fstab                                  

# /etc/fstab: static file system information.


#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3


UUID=c6268024-c8f5-4c30-862b-685155f3286d /               ext3    defaults,erro$
# /dev/sda6
UUID=19a7003b-bed0-4595-b3ec-65424b116038 none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0









                               [ Read 10 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by taurus on 2006-12-14
What are the two partitions you want to mount?

```
sudo fdisk -l
```

---

### Post by unshaven123 on 2006-12-14
the partion is sda5 and the hard drive is sdb1

---

### Post by unshaven123 on 2006-12-15
Thank you to all who have posted to help me by following the links posted i have solved the problem of mounting my windows drives and partitions by doing a clean install of ubuntu with a manual partition of the hard drive and mounting the other drives at the same time 

not quick or elegant but given my current knowledge of linux best way for me

---

