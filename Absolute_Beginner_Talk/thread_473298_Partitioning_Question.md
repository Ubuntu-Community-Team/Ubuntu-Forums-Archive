---
title: "Partitioning Question"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by gasnmyveins on 2007-06-13
6.06LTS      320GB HD NTSF with only ten gigs of pics.

 When the partitioner starts, I tell it to automatically resize the partition it sets itself to 159.4 gigs. When I click "next", it gives me an error message saying "failed to create enough space for installation." It has done this several times. What should I do? Thanks.

---

### Post by pkarjala on 2007-06-13
Can you list of all of your current partitions, sizes, and the type of formatting they have?

IE:

Partition 1:  FAT32  32MB
Partition 2:  NTFS  125GB

Also, is your drive an IDE, SCSI, or SATA?

---

### Post by Inxsible on 2007-06-13
if you are using the liveCD, go to applications->accessories -> terminal and type in the following command and post the output here
```
sudo fdisk -l
``` -l is lowercase L

---

### Post by gasnmyveins on 2007-06-13
pkarjala-  It's all one NTSF partition on an IDE drive. No OS on it, just ten gigs of family pics.

Inxsible- I'll go try it now. Thanks for the heads up about the lower case "L". I thought it was a 1.

---

### Post by Inxsible on 2007-06-13
> **gasnmyveins said:**
> pkarjala-  It's all one NTSF partition on an IDE drive. No OS on it, just ten gigs of family pics.

Inxsible- I'll go try it now. Thanks for the heads up about the lower case "L". I thought it was a 1.

You might wanna backup those pictures. You never know what might happen and I am sure you dont wanna lose 10GB worth of your family pics

---

### Post by gasnmyveins on 2007-06-14
I burnt them to dvd, and just checked. They're OK. I still don't want to delete them, though.

 Here's what it said. BTW, I've never seen a lower case "L" rendered like that before. I thought it was some goofy symbol I didn't have.

 Disk /dev/hda: 320.0 GB 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot          Start               End            Blocks             ID       System
/dev/hda1   *                1             38913        312568641         6         FAT16
ubuntu@ubuntu:-~$

---

### Post by Inxsible on 2007-06-14
> **gasnmyveins said:**
> I burnt them to dvd, and just checked. They're OK. I still don't want to delete them, though.

 Here's what it said. BTW, I've never seen a lower case "L" rendered like that before. I thought it was some goofy symbol I didn't have.

 Disk /dev/hda: 320.0 GB 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot          Start               End            Blocks             ID       System
/dev/hda1   *                1             38913        312568641         6         FAT16
ubuntu@ubuntu:-~$

You are not planning to install Windows are you ? 

fdisk says that Windows installation is present on the drive. You notice the Boot flag * ?

Anyway, you can use the GParted which is on the live CD to shrink the current partition to whatever size you want. Then use the remaining space to install Ubuntu.

have you decided what partitions you want and what sizes you want them to be ?

Have a look here for more info on 
[Partitioning]("www.psychocats.net/ubuntu/partitioning")

[Installling]("www.psychocats.net/ubuntu/installing")

---

### Post by gasnmyveins on 2007-06-14
Nope, not planning to put windows on it. I have windows on my other drive, which crashed. This one was a slave which I was using for additional storage. Now I want to put ubuntu on part of it, and leave part for picture storage. I suppose 100 gigs would be good for ubuntu.
 I don't understand why the drive has a boot sector on it, since I never installed an OS on it. Strange. I also don't understand why the installer gives me that error message. I guess it would help if I had a little computer knowledge. Then again, I'm hoping to get some as I go along with linux. 
That "Gparted" that you mentioned.... is that the option for manually editing my partition, or is it the total partitioner program?  Thanks.
 Thanks for the links, too.

---

### Post by Inxsible on 2007-06-14
> **gasnmyveins said:**
> Nope, not planning to put windows on it. I have windows on my other drive, which crashed. This one was a slave which I was using for additional storage. Now I want to put ubuntu on part of it, and leave part for picture storage. I suppose 100 gigs would be good for ubuntu.
 I don't understand why the drive has a boot sector on it, since I never installed an OS on it. Strange. I also don't understand why the installer gives me that error message. I guess it would help if I had a little computer knowledge. Then again, I'm hoping to get some as I go along with linux. 
That "Gparted" that you mentioned.... is that the option for manually editing my partition, or is it the total partitioner program?  Thanks.
 Thanks for the links, too.

its the partitioner. Go to System --> Preferences --> GParted. or maybe System- --> Administration --> GParted.  I never seem to rbr where it is exactly.

---

### Post by gasnmyveins on 2007-06-14
OK, Gparted crashed once then ran. Scratch that. It crashed again. Try, try again.

---

### Post by Inxsible on 2007-06-14
what speed did you burn the livecd iso at ? Recommended speed is 4x or less

---

### Post by gasnmyveins on 2007-06-14
Now it want to know which partition to use for my new installation. I only had one, and it only lists one at 320 gigs. It says I must mount on partition on the root file system, and must choose one partition for use as swap space. I also have 2 drop down menus, but don't know what to do with them.
 It also has a check box labeled "reformat." Should I check it? When I clicked the forward button, it said "No root file system."

---

### Post by gasnmyveins on 2007-06-14
> **Inxsible said:**
> what speed did you burn the livecd iso at ? Recommended speed is 4x or less

I didn't know that. I think it was usually burning around 8x.

---

### Post by Inxsible on 2007-06-14
did you check the link i gave you earlier for installing ? It lists all the screenshots. Have a look there

---

### Post by Inxsible on 2007-06-14
you will have to first shrink the partition so that your pics will be saved..then out of the remaining space, you will need to create 

root partition -- denoted by /
and a swap partition

it is good practice to have a separate /home partition too.

swap should be about 1.5 times your RAM

---

### Post by gasnmyveins on 2007-06-14
I looked at them, but they both seemed at aimed dual boot setups.

---

### Post by Inxsible on 2007-06-14
Well in the installation you can select largest contiguous free space, which will take the freespace and install it there. You will first need to create that free space with GParted.

---

### Post by gasnmyveins on 2007-06-14
It's not givng me that option. It only gives me 3 options. Resize master and use freed space. That one says "Failed to create enough space for installation." #2 is "Erase entire disk." #3 is "Manually edit partition table.

---

### Post by gasnmyveins on 2007-06-14
I'm going to have to work on this tomorrow. I need to get up for work in about 5 1/2 hours. Thanks for your help. This will get done sooner or later.

---

