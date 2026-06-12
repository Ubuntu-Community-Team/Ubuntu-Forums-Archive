---
title: "addring drives to RAID 1 - QUESTIONS"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2007-10-10
i want to add 2 new drives to a raid 1 array.


some basic info
**sudo mdadm --detail --scan**
```

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=ac975da7:73b2afe8:27238c36:9a27862a

```


**/etc/fstab**
.```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda2
UUID=f5d37998-8fe9-4beb-b18b-93c7f33ccda1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sdb1
UUID=1b6feab2-9970-40d1-afb6-bb53e2a7319b /data ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdc1
#UUID=b88c73d7-39a9-447f-b108-bae4a67708a3 /raid1 ext3 nouser,usrquota,atime,noauto,rw,dev,exec,suid 0 2
# /dev/sdd1
#UUID=b88c73d7-39a9-447f-b108-bae4a67708a3  ext3 nouser,usrquota,atime,noauto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=0558cccf-3453-4452-8d11-1e61618aecd8 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
# raid
/dev/md0        /mnt/raid       ext3    defaults,usrquota 0 2

```


**proc/mdstat**
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdc1[0] sdd1[1]
      732571904 blocks [2/2] [UU]

unused devices: <none>
```

I have not connected the drives yet.

1) once connected to the machine - how do i get the machine to recognize the drives?
2) once the drives show up in /etc/fstab, can i then add the drives to the array using mdadm?
3) once i have successfully added the raids to the array can i use mdadm grow?  

i found a good raid 1 + grow post on the forum - but i need more info on how to get the disks into FSTAB (i think)

pls advise...

---

### Post by huggy77 on 2007-10-15
i successfully mounted the 2 new drives i want to add to the raid.

i also formatted them

i then ran  (it is actually still running):
```
mdadm --grow /dev/md0 --size=max
```

i guess i have to run:
```
resize2fs /dev/md0
```

is that it?  am i missing something?

---

### Post by huggy77 on 2007-10-17
Dont tell me i stumped you guys... Cant be that hard a questions

---

### Post by psusi on 2007-10-18
I have no idea what in the world you are trying to do.  What is it that you are trying to grow?  If you are building a new array, then you  just run mdadm once and give it the two drives and it initializes them and activates the array.  Then you format /dev/md0 and add it to fstab.

---

### Post by huggy77 on 2007-10-18
i am sorry - i guess i should have been more clear when i stated > i want to add 2 new drives to a raid 1 array.
:lolflag:


i need to add 2 new drives to an existing raid 1 array that currently has 2 ext3 drives with data on.  What are the steps...

---

### Post by Quikee on 2007-10-18
If you have a existing RAID 1 array of 500 GB for example and add 2 more drives you still have a RAID 1 array of 500 GB - but 4 drives mirrored. Why do you think you need to grow something. ;)

---

### Post by huggy77 on 2007-10-18
because i am a putZ....

I just assumed that if i added 2 more drives my capacity would increase....  

i currently have 1 drive mirroring another drive...  750 gb of mirrored data... i would like this drive to become 1.5 tb of mirrored data....  I have 2 more 750 gb drives in the array..  do i have to set up something other then raid 1?

---

### Post by Quikee on 2007-10-19
> **huggy77 said:**
> because i am a putZ....

I just assumed that if i added 2 more drives my capacity would increase....  

i currently have 1 drive mirroring another drive...  750 gb of mirrored data... i would like this drive to become 1.5 tb of mirrored data....  I have 2 more 750 gb drives in the array..  do i have to set up something other then raid 1?

RAID 10 - which is in your case 2x RAID 1 array in a RAID 0. I think this is what you wanted now. The good thing is that a RAID 0 will speed up everything and you also have some data loss protection with 2 drives failing, but they must not be in the same RAID 1 array. I don't know if you can make this array losslessly - without removing all data before creation. 

or 

RAID 5 - which will create you a array with 3 disc capacity and one drive failure data loss prevention. If you lose 2 drives all the data is lost. I think you can migrate a RAID 1 to RAID 5.

or

RAID 6 - which will create you a array with 2 disc capacity and two drive failure data loss prevention. If you lose 3 drives all the data is lost. This is the most "secure" in your situation (if you don't want to create an array with 4 mirrored discs ;) ) but you also sacrifice the most speed.

For further information see this [RAID howto]("http://tldp.org/HOWTO/Software-RAID-HOWTO.html")

---

### Post by huggy77 on 2007-10-19
i am so angry with myself.  i was running a vanilla raid 1 and i ended up with a fantasically secure set up of one data drive that had 3 mirrors... Talk about redundancy...

new approach - (these damn 750 gb drives take for ever to set up)
i failed one of the drives from my 4 disk array - then i removed it and mounted it as a 1disk array as /mnt/temp

i then took the remaining disks and created a raid 5 out of them - also reformatted that array to XFS.

After my new raid recovers - i will move all that data from temp to the new raid.  lastly i will format the temp drive then add it to the new array as per:
[http://scotgate.org/?p=107](http://scotgate.org/?p=107)

---

### Post by huggy77 on 2007-10-19
quick question - i keep running  cat /proc/mdstat to view the status - is there anyway to auto refresh that... i want it to auto refresh to keep me posted on the status....  Is there a way to auto-refresh cat /proc/mdstat????

---

### Post by garretwp on 2007-10-22
It is probably late in adding advice to refresh the cat /proc/mdstat. But I will add it anyway. if you do "watch cat /proc/mdstat" it will refresh the screen every 2sec.

- Garrett

---

### Post by huggy77 on 2007-10-22
that is exactly what i was hoping for...  THanks much!

---

