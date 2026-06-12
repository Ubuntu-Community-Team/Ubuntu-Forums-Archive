---
title: "Partition loss"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Nermin on 2008-03-14
Hello, I'm not sure if this belongs here, but here I go.

I tried to install Ubuntu 7.10, and when it came to where to install, I tried to make a new partition and i did succed, but i made some mistake and now i have lost 40Gb disk space... I tried to make a dual boot, also Vista can't find the lost space. It was empty, so i didnt lose any data, but the 40 Gb. So, is there any way to get it back???

Thanks

---

### Post by scragar on 2008-03-14
install gparted:```
sudo apt-get install gparted
```and see if it's just unassigned space somewhere, either way gparted will tell you where it has gone if you look.

---

### Post by joshrobinson on 2008-03-14
> **Nermin said:**
> Hello, I'm not sure if this belongs here, but here I go.

I tried to install Ubuntu 7.10, and when it came to where to install, I tried to make a new partition and i did succed, but i made some mistake and now i have lost 40Gb disk space... I tried to make a dual boot, also Vista can't find the lost space. It was empty, so i didnt lose any data, but the 40 Gb. So, is there any way to get it back???

Thanks

```
sudo apt-get install gparted
```
then
```
sudo gparted
```
this will show you your partition table, and will show if there really is any free space missing, it will probably say "unpartitioned space" be very careful here, and dont make changes unless you know what your doing, let me know what it shows

---

### Post by Duck2006 on 2008-03-14
When you partitioned the drive, did you partition  it from within vista?

---

### Post by Nermin on 2008-03-14
wow,so many responses:) thank you. After that i did not install Ubuntu, i wanted to give ubuntu that 40 Gb, and when i could not i stopped. When i try to install and come to the partition page it shows me the space and it says Unused or free space, i am not that sure, i did it last week and didnt have time until now. So, i see the space, but cant do anything with it. I cant create the swap part. If I am unclear, i am sorry, i will try it tomorrow again and post how it is exactly written.

---

### Post by Duck2006 on 2008-03-14
You should be able to partition the space you made for ubuntu from the live cd. If you have problems doing it with that, try doing it with the gparted live cd.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Nermin on 2008-03-14
because i am planing to install ubuntu either way, can i get the space back after i install ubuntu? To get the space for vista and use other space for ubuntu. i hope i am not complicating things... can i do that with gparted when i install ubuntu without the live cd?

---

### Post by Duck2006 on 2008-03-14
Install ubuntu on to what space you want and add the rest back to vista from within vista.

This may help.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by Nermin on 2008-03-14
i am installing it right now. so, i come to the prepare disk space page, choose manual and get this

Device        Type  Mount point  Format  Size        Used

dev sda
dev sda 1   ntfs   media sda1             12582      7300
dev sda 2   ntfs   media sda2             159016    53800
dev sda 4   ntfs   media sda4             35000      28800
free space                                        43456

so, the space is there, what with it??? can i make ubuntu out of that?

---

### Post by Nermin on 2008-03-14
when i make a new partition out of the free space and want to proceed it says

No root file system is defined.
Please correct this from the partitionig menu.

If i cant make with this, i will resiye in vista and install it that way, but i would like to try this first. So, thanks.

---

### Post by Nermin on 2008-03-14
Update i just had to point a / as a mount point and i cant create any swap space but i continued without it. When i want to install it says this


The ext3 file system creation in partition #3 of SCSI1 (0,0,0) (sda) failed.



and it gets me back to the prepare disk space.
what now?

---

### Post by Duck2006 on 2008-03-14
Are you doing this from the ubuntu live cd?

---

### Post by Nermin on 2008-03-14
yes. because yes would be too short as a message, it feels weird i type this text extra...:)

---

### Post by Duck2006 on 2008-03-14
Try make the partitions with the gparted live cd it will go a lot smoother.

---

### Post by Nermin on 2008-03-14
i believe that, but is it somehow possible this way? and should i be able to retrieve my lost disk space that way? i could install ubuntu using some more disk space from vista, but i dont want to lose the 40 gb...

---

### Post by Duck2006 on 2008-03-14
You will have to unmout the drive befor you can partition and format the drive. from the live cd in the terminal type.

sudo fdiak -l

and post the output here.

---

### Post by Nermin on 2008-03-14
it just starts a new row.

and when i copy what you wrote, the command, it says

sudo: fdiak: command not found

i can start gparted from here too and it shows all partitions, the last is

/dev/sda3  (a warning sign here) the filesystem is unknown and the size is 40 gb, i can delete it, but i am not sure what will happen...

---

### Post by bodhi.zazen on 2008-03-14
There was a small typo, the command is :

```
sudo fdisk -l
```

That is a small "L" not a 1.

That command will list your partitions. My guess is you have a new partition, Windows can not read linux file systems (unless you install a driver).

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Nermin on 2008-03-14
thisis what i got

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9ff934a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       20863   155289600    7  HPFS/NTFS
/dev/sda3           25119       30401    42435697+  83  Linux
/dev/sda4           20863       25118    34179687+   7  HPFS/NTFS

Partition table entries are not in disk order

i guess you are right because vista cant see the missing space. and what should i do now? even when vista does see it, can i bring the space back with the disk manager?

---

### Post by bodhi.zazen on 2008-03-14
You can do what you want with the space, install Ubuntu or restore it to Vista.

You can restore it to Vista with Gparted, which is on the live Ubuntu CD, by deleting the partition and adding the free space back to your NTFS (Vista) partition.

Windows does not have the drivers to "see" any file systems other the FAT or NTFS. 

There is nothing "wrong" with your hard drive.

Gparted Documentation : [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by Nermin on 2008-03-14
so when i delete it with gparted, is it going to get back automaticly on vista? i cant install ubuntu with it because of the error i posted earlier... i want to use that space for ubuntu so i would prefer to install on it ubuntu now, rather then add it back to vista and then create again a partition for ubuntu.

---

### Post by bodhi.zazen on 2008-03-14
1. No, if you delete the partition it will not be added back to Vista. You would need either to resize your Vista NTFS partition or add the space as a new partition (which would be E:\)

2. My guess with your error is that the partition is mounted.

Unmount it and re-try

You can un-mount the partition from gparted ....

---

### Post by Nermin on 2008-03-14
sorry, but, how do i un-mount it? i am in gparted and i can only delete it or format to sth else. also, if i wanted to give it back to vista, do i delete it first and then resize the vista partition? and could i lose it for good if i delete it? again, i am sorry, but i didnt work with partitions until now...

---

### Post by Nermin on 2008-03-15
Thank you all very much. I fixed it with gparted. Thanks again.

---

### Post by Nermin on 2008-03-15
i still cant install ubuntu. No matter which method i try, i always get this message

The ext3 file system creation in partition #7 of SCSI1 (0,0,0) (sda) failed.

the partition manager is different, but its always the same message. I tried to create a partition with gparted, to create it manually and to use the Use most continued disk space command. What now??? i cant find any help...

---

