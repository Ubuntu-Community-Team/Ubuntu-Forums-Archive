---
title: "gutsy install"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by rojo1943 on 2008-01-07
I've installed guysy on a 20 gig hard drive and everything works great but!!!
   the installation used 8.5 gig of space and the rest is unused. Using gparted , it shows two ext3 files (one locked and one unlocked) and two swap files ( one locked and one unlocked)
Is there  anyway I can ise all 20 gig of space??? Thanks in advance

---

### Post by stump138 on 2008-01-07
sounds like you might have partitioned your drive twice during the install, can you post the contents listed when you type:
```
sudo fdisk -l
```
at a terminal please?

---

### Post by rojo1943 on 2008-01-07
Device          boot                 start          end          blocks               id               system
/dev/hda1                                         1        1110         8916043          83               linux
/dev/hda2                                   2284        2432         1196842           5                extended
/dev/hda3           *                      1111        2283         9422122          83               linux
/dev/hda5                                   2343        2432         722893            82               linux swap/solaris
/dev/hda6                                   2284        2342         473854            82               linux swap/solaris

---

### Post by p_quarles on 2008-01-07
The results of the following commands would also be useful:
```
cat /etc/fstab
```
and 
```
df -h
```
Also, since it appears you have two swap files for some reason, I'm curious to see the output of 
```
free
```

---

### Post by rojo1943 on 2008-01-07
free              total                used             free         shared        buffers         cached
mem:          247812           243692            4120           0            604               65188
-/+  buffers/cache            177900            69912
swap:         473844           35644             438200




filesystem                          size             used              avail            use%                  mounted on

/dev/hda3                         8.9G            2.4G              6.1G              29                           /
varrun                              121m            80k               121m               1                       var/run
varlock                              121m             0                  121m              0                       var/lock
udev                                  121m           60k               121m               1                       /dev
devshm                             121m            0                   121m               0                      /dev/shm
lrm                                     121m           34m              88m                  29                  /lib/modules/2.6.22-14

---

### Post by p_quarles on 2008-01-07
Okay, it looks like the other partition you noticed simply isn't mounted. Again, post the output of 
```
cat /etc/fstab
```
There should be an easy fix.

---

### Post by rojo1943 on 2008-01-07
#  /etc/fstab:  Static file system infomation
#
#  <file system> <mount point>      <type>    <options>          < dump>        <pass>
proc                     /proc                        proc          defaults              0                      0

# /dev/hda3
uuid=5718cf50-1984-493e-8979-7cac50381e14 /                         ext3            defaults,error
s=remount-ro 0               1

# /dev/hda6
uuid=5a3cad14-eb0e-4d9a-bf29-c57822678203    none                  swap              sw

       0                 0

/dev/hdc                 /media/cdrom0          udf, iso9660  user , noauto ,exec    0          0

/dev/fd0                 /media/floppy0           auto              rw, user , noauto , exec  0       0

---

### Post by p_quarles on 2008-01-07
Okay, first you'll need to get the uuid of your unused partition. You can get that by running:
```
ls -l /dev/disk/by-uuid
```
The uuid is going to be the long code between the timestamp and and the "->". Make a note of the uuid for the disk called "/hda1" as you'll need that for one of the next steps. 

Second, it'll be a good idea to make a custom mount point for this partition, so that you can use it for storing your own data rather than for any OS-level purposes. So, make a mount directory for it:
```
sudo mkdir /media/data
``` 
Then, make sure you have access to this directory:
```
sudo chown *your-username* /media/data
```
Now, you'll need to add an entry to /etc/fstab:
```
gksudo gedit /etc/fstab
```
Add the following:
```
#/dev/hda1
uuid=(insert the code you got from the first step) /media/data ext3 defaults 0 2
```
You'll have to reboot before it's mounted this way, but you also make sure it works by mounting the partition manually:
```
sudo mount /dev/hda1 /media/data
```
Hope this is all clear. Ask if you have any further questions.

---

### Post by rojo1943 on 2008-01-07
Thanks to all  Problem solved

---

