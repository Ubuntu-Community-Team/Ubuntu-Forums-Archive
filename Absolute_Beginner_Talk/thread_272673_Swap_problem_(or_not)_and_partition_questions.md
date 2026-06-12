---
title: "Swap problem (or not) and partition questions"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by raul_ on 2006-10-06
Ok i know u're gonna laugh when u read this but............i think i may not have a swap partition. When i installed ubuntu (in the hoary ages) it didn't ask me for a separate swap or home partition, so i just mounted / and no questions asked. The other day, i was trying to install dapper from the cd for a friend, and it says that i MUST have a partition for swap. wtf? lol. and that just bugs me because i don't know how's that affecting my system. Cold any1 clarify this?

One other question:

is there a GREAT advantage in having your home folder in a separate partition (instead of the obvious of course, if ur system is damaged and u need to format ur disc). and if i already have it in one partition, can i just copy/paste it to another?

---

### Post by bodhi.zazen on 2006-10-06
> **raul_ said:**
> Ok i know u're gonna laugh when u read this but............i think i may not have a swap partition. When i installed ubuntu (in the hoary ages) it didn't ask me for a separate swap or home partition, so i just mounted / and no questions asked. The other day, i was trying to install dapper from the cd for a friend, and it says that i MUST have a partition for swap. wtf? lol. and that just bugs me because i don't know how's that affecting my system. Cold any1 clarify this?

Just check fstab:```
gedit /etc/fstab
```

If you are not sure, post the contents of fstab.

> **raul_ said:**
> One other question:

is there a GREAT advantage in having your home folder in a separate partition (instead of the obvious of course, if ur system is damaged and u need to format ur disc). and if i already have it in one partition, can i just copy/paste it to another?

IMO no. /home contains a mix of hidden configuration files and data.

IMO there is utility in a /data partition. Most, if not all, of the config files in /home do not need to be backed up. You know the ones that do (becaue you modified them).

IMO a /home partition is over rated, BUT use of a /data partition is under rated.

If you like, you can always back up your /home in /data with tar.

---

### Post by raul_ on 2006-10-07
Ok here's what in fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext2    defaults,errors=remount-ro 0       1


and then my windows and cdroms...i guess i don't have a swap partition after all =\ how's that affecting my system?

---

### Post by anaconda on 2006-10-07
If you have enough RAM (say >1,5GB) then you dont really need any swap

However..
Here is instructions how to make a swap file after installing ubuntu:
[http://www.ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap+file](http://www.ubuntuforums.org/showthread.php?t=265051&page=2&highlight=swap+file)
It is just as good as separate swap-partition, and you can adjust its-size by deleting it and creating smaller/bigger anytime..

Oh. and the instruction works. dont know why he had problems with the dd -command.. dd is just basic copy command..

---

### Post by raul_ on 2006-10-07
Segmentation fault in the first intruction :P :

root@raul:/home/raul # dd if=/dev/zero of=/swapfile bs=1024k count=256
256+0 records in
256+0 records out
Falha de segmentação


I suppose i can't use gdb on this case 8-)

---

### Post by bodhi.zazen on 2006-10-08
Use the live CD to resize your Ubuntu partition and make a swap partition.

Size = RAM X2, max 1 Gb.

Add this line to fstab:
```
sudo gedit /etc/fstab
```
Add this line:
> /dev/hdxy  swap  swap  defaults  0 0
Where hdxy is your swap partition.

reboot.

---

