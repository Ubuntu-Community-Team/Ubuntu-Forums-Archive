---
title: "partition help please"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-11-19
ok i attached a screenshot of gparted to help. What i want to do is merge the unallocated space together so i can format it to ext3 and use it for some of my music and files. The reason it is way over on the right is i made a separate /home for ubuntu and resize my / from 22GB to what you see there (9.7GB). when i try to create a partiton so i can move it i get the error that i can only have 4 partitions and i need to make a extended partition....i dont know how to do that.

also something to keep in mind,,,

1) i cant get gparted to run on my live cd because i only have dial up and it work work on the live cd.

2) i used mandriva to resize my ubuntu /

3) i can get the graphical interface of my gparted boot CD to work....wont load x server.

im not an expert on partitioning so i just need some hot-to's and advice about what i should do.


also is there a way i can use only one swap partition for both ubuntu and mandriva? if so how would i do this?
thanks for your time! :)

---

### Post by Sef on 2007-11-19
> when i try to create a partiton so i can move it i get the error that i can only have 4 partitions and i need to make a extended partition....i dont know how to do that.

Not quite true about 4 partitions.   You can only have 4 primary partitions.  You can have as many extended partitions as you like.   Another name for an extended partition is a logical partition.  

What you would have to do is delete one of your primary paritions and create a logical parition.  

Before doing anything else, **back up** your data.

---

### Post by natehatewindows on 2007-11-19
ok so if i need to delete a partition first then how could i make both run off of one swap? and how do i create a logical with gparted?

---

### Post by aa.ivanov on 2007-11-19
In order to merge the unused space you'll have to move sda1, sda3 and sda4 to the end of the disk. Since these are /, /home and swap you will have to boot from a CD - you cannot resize partitions that are mounted i.e. in use.

Since you already have used all 4 primary partitions (these are sda1 - sda4) you'll have to create logical one. To do this you'll have to enlarge the extended partition sda2 to include the free space and then create a logical partition inside the extended one.

Since you have trouble with starting gparted live cd - try using some other live cd. Knoppix for example has a reputation of very robust in terms of correctly recognizing hardware. The ultimate boot cd is another option packed with a lot of useful software, though a bit harder to use than knoppix.

Yes you can use one swap partition for both. You'll need to point both your linuxes to the same partition. In the distro whose partition you're deleting open /etc/fstab for editing (you'll need root privileges) and locate the row where swap is described and correct the sda number. Then you can happily delete the unused swap partition

EDIT: Another scenario might be:
[LIST=1]
[*]delete the sda3 swap partition,
[*]move the sda1 right after the sda2
[*]move sda3 to the end of the disk
[*]create a new par
[/LIST]tition with the free space

I would preffer the scenario I've described above.

---

### Post by aa.ivanov on 2007-11-19
> **Sef said:**
> Another name for an extended partition is a logical partition.

Not quite. You're right - *primary partitions *are limited to 4. It's a silly rule as old as I am. Extended partitions were developed as a workaround for this issue. Extended partition is a primary partition that's used as a container for logical partitions. 

In the case of our friend here the extended partition is sda2 and sda5 and above are logical partitions.

---

### Post by natehatewindows on 2007-11-19
so i can just use mandriva to move my ubuntu to the end of the drive right? no need for a boot disk if i have two distros?

---

### Post by natehatewindows on 2007-11-19
here is my ubuntu fstab, i should jus change the red to /dev/sda7 to use the other swap? thats all? and reboot?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=27c96fda-9808-4018-a7cf-737a53434618 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=BC0816BF0816791A /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
#[COLOR="Red"] /dev/sda3[/COLOR]
UUID=e0c6a6ab-e798-4e88-91ae-798adb4556f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1       /home    ext3     nodev,nosuid  0  2

---

### Post by aa.ivanov on 2007-11-19
> **natehatewindows said:**
> so i can just use mandriva to move my ubuntu to the end of the drive right? no need for a boot disk if i have two distros?

Yes, as long as you don't need to deal with the partitions that are used (aka mounted) by mandriva.

A reminder:
Moving partitions around is a sensitive operation. Power outage for example can result in data corruption in the partitions you're moving. Highly recommended is to have a backup of all valuable data.

---

### Post by natehatewindows on 2007-11-19
also about moving them.....i just was playing in gparted with my sda2 and i did the resize/move option just to see what it would be like. how do i move it? it only lets me drag the thing to resize it. do i need to resize it and then resize the other way?

---

### Post by natehatewindows on 2007-11-19
also why did mandriva automatically create a extended partition?

---

### Post by aa.ivanov on 2007-11-19
> **natehatewindows said:**
> here is my ubuntu fstab, i should jus change the red to /dev/sda7 to use the other swap? thats all? and reboot?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=27c96fda-9808-4018-a7cf-737a53434618 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=BC0816BF0816791A /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
#[COLOR="Red"] /dev/sda3[/COLOR]
UUID=e0c6a6ab-e798-4e88-91ae-798adb4556f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1       /home    ext3     nodev,nosuid  0  2

Yes

> **natehatewindows said:**
> also about moving them.....i just was playing in gparted with my sda2 and i did the resize/move option just to see what it would be like. how do i move it? it only lets me drag the thing to resize it. do i need to resize it and then resize the other way?
Hmmm I have not resized/moved partitions with parted... and I'm stuck on a winxp machine here at work :(
I think, when you open the resize/move dialog you should be able edit the start sector of the partition which should result in moving the partition.

---

### Post by natehatewindows on 2007-11-19
ok that makes sense.....thanks a lot for you help. ill try it in the morning.....wife will get mad if im doing this tonight ;)

---

### Post by aa.ivanov on 2007-11-19
> **natehatewindows said:**
> also why did mandriva automatically create a extended partition?

It's a policy in most linux installers to use logical partition as much as possible. Almost all decent dostros create just / and/or /boot partition as primary and throw almost everything else on logical partitions or even on LVMs. That's as much as I can say. I'm not familiar with the exact logic deployed in different installers. :(

---

### Post by natehatewindows on 2007-11-19
well i guess it could have done it  because there was not enough room, there was already 3 primarys :)

and,,,,

why doesn't ubuntu do that?!?  ;)

---

### Post by natehatewindows on 2007-11-20
ok now i have been trying to move my mandriva partition (dev/sda2) just to see how gparte moves them, but it wont move, only expand it. I try to put 38829MB preceding the partition but it wont let me. how do i move partitions with gparted?

thanks!

---

### Post by natehatewindows on 2007-11-20
anyone?

---

