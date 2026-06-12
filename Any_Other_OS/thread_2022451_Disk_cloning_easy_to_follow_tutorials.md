---
title: "Disk cloning easy to follow tutorials"
date: 2012-07-11
forum: Any Other OS
---

### Post by tech291083 on 2012-07-11
Hi,

I have already downloaded the CloneZilla iso and burnt it to a CD. i want to learn how to clone a HDD. I have one HDD SATA with 80 GB space and another with 500 GB space. I want to know if there are different OS on different partitions on one HDD such as Win 7/XP and Linux (80 GB in my case), can it still be clone bit by bit to a bigger or same size HDD? Is there a good video/ text tutorial that I can follow? I have never cloned a hard drive before. Is there any other easy to use free cloning tool apart from CloneZilla CD based on your experience? Thanks.

---

### Post by CharlesA on 2012-07-11
They have excellent documentation here:

[http://clonezilla.org/](http://clonezilla.org/)

[http://clonezilla.org/screenshots.php?in_path=/00_Clonezilla](http://clonezilla.org/screenshots.php?in_path=/00_Clonezilla)

---

### Post by nm_geo on 2012-07-12
> **tech291083 said:**
> Hi,

  can it still be clone bit by bit to a bigger or same size HDD? Is there a good video/ text tutorial that I can follow?..

Clonezilla can do both.. bit by bit.. partitions.. or complete HDD 

 I have never cloned a hard drive before. 

You will like it after you do.  I Clone mine main 320GB HDD to a spare same size maybe once a month..

Is there any oe ther easy to use free cloning tool apart from CloneZilla CD based on your experience? Thanks.

My experience is that Clonezilla is by far the best including the ones you pay for. You can even put it on a USB which is much faster.  The websites listed above are great too.

---

### Post by Shadius on 2012-07-12
CloneZilla is very good for cloning. I've also used G4L (Ghost 4 Linux). Both are very good. Here's a nice little tutorial I've used before when using Clonezilla. 

[How To Use Clonezilla Tutorial]("http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/")

I suggest you read a little bit of the Clonezilla documentation before diving into it. It helps in the long run! Good luck!

---

### Post by tech291083 on 2012-07-12
> **Shadius said:**
> 
Here's a nice little tutorial I've used before when using Clonezilla. 

[How To Use Clonezilla Tutorial]("http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/")

I suggest you read a little bit of the Clonezilla documentation


Thanks for the tutorial. Looks ok to me. I have a few questions to ask, please help me here. 

As far as I know, I need to keep both the hard drives connected to my motherboard (source drive - 80 GB SATA, destination drive 500 GB SATA) before I start cloning process. I do not have a USB pen drive or any other medium as mentioned in the tutorial (or I seem to have misunderstood something here). I only have two drive to complete the cloning process. I will wipe/format the destination drive with GParted Live CD ie delete all the partitions if any on it.

Please suggest me anything you like before i actually dive into the unknown, thanks.

---

### Post by Shadius on 2012-07-12
> **tech291083 said:**
> Thanks for the tutorial. Looks ok to me. I have a few questions to ask, please help me here. 

As far as I know, I need to keep both the hard drives connected to my motherboard (source drive - 80 GB SATA, destination drive 500 GB SATA) before I start cloning process. I do not have a USB pen drive or any other medium as mentioned in the tutorial (or I seem to have misunderstood something here). I only have two drive to complete the cloning process. I will wipe/format the destination drive with GParted Live CD ie delete all the partitions if any on it.

Please suggest me anything you like before i actually dive into the unknown, thanks.

Forget that tutorial that I posted. It will confuse you. Use this one instead: [Disk To Disk Clone]("http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone"). You basically have it right. Make sure both hard disk drives are connected, the source and the destination. I've always prepared the destination drive to receieve the data first, so you can do that as well. Use GParted or whatever tool you are comfortable with to format the destination drive to the desired filesystem.

---

### Post by tech291083 on 2012-07-12
> **Shadius said:**
> 
Use this one instead: [Disk To Disk Clone]("http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone"). 
Make sure both hard disk drives are connected, the source and the destination. I've always prepared the destination drive to receive the data first, so you can do that as well. Use GParted or whatever tool you are comfortable with to format the destination drive to the desired filesystem.

Ok, thanks.

You have understood me. I just have two internal hard drives and both in my pc ie connected to the motherboard via SATA connectors. I have no external USB hard drive. My source drive (80 GB) has Fedora 16 on it and it occupies the whole drive as the only OS on it. It was installed using the Use entire disk option few months ago and I think it has LVM partitions. There is no Windows. This drive is to be cloned to a bigger 500 GB internal drive. That is all I want to do. So I think it is device to device method.  

I will use GPared CD and will format the whole drive (500 GB one) and keep it empty, formatted. I do not intend to create any partition or file system on the destination drive. Is this the right thing to do?

I think I need to boot the pc using source hard drive with Fedora 16 on it and then insert the CloneZilla CD and reboot my pc, right? My destination drive is totally empty has no OS or anything else on it.

Thanks a lot.

---

### Post by Shadius on 2012-07-12
> **tech291083 said:**
> Ok, thanks.

You have understood me. I just have two internal hard drives and both in my pc ie connected to the motherboard via SATA connectors. I have no external USB hard drive. My source drive (80 GB) has Fedora 16 on it and it occupies the whole drive as the only OS on it. It was installed using the Use entire disk option few months ago and I think it has LVM partitions. There is no Windows. This drive is to be cloned to a bigger 500 GB internal drive. That is all I want to do. So I think it is device to device method.  

I will use GPared CD and will format the whole drive (500 GB one) and keep it empty, formatted. I do not intend to create any partition or file system on the destination drive. Is this the right thing to do?

I think I need to boot the pc using source hard drive with Fedora 16 on it and then insert the CloneZilla CD and reboot my pc, right? My destination drive is totally empty has no OS or anything else on it.

Thanks a lot.

Yes, you understand it correctly. Yes, boot up your system regularly, then insert the Clonezilla LiveCD, then reboot. You will be booted into the Clonezilla LiveCD. Then you can begin the process of cloning. Make sure you take note of what your source drive is named and what your destination drive is named. Most likely your source drive will be ***sda*** and your destination drive will be, ***sdb***.

---

### Post by CharlesA on 2012-07-12
> **Shadius said:**
> Yes, you understand it correctly. Yes, boot up your system regularly, then insert the Clonezilla LiveCD, then reboot. You will be booted into the Clonezilla LiveCD. Then you can begin the process of cloning. Make sure you take note of what your source drive is named and what your destination drive is named. Most likely your source drive will be ***sda*** and your destination drive will be, ***sdb***.

Yep.

It will also tell you the size and model of the drives, as well as the label, if any. I usually go off the size and/or label/model when cloning.

---

### Post by Shadius on 2012-07-12
> **CharlesA said:**
> Yep.

It will also tell you the size and model of the drives, as well as the label, if any. I usually go off the size and/or label/model when cloning.

Yup, I usually do the same. :)

---

### Post by tech291083 on 2012-07-14
Ok friends,

Just did the cloning for the first time ever in my life using Clonezilla CD and it was successful but took me 2 hrs and 42 mins, do not know why so long?

I used a 80 GB SATA HDD (internal) with Fedora 16 on it as the only OS occupying the whole of this HDD as source and a 500 GB SATA HDD (internal), which I formated using the GParted CD (by creating a new partition table and making the whole 500 GB unallocated space, did not actually create any partitions as such). 

I used the device-device option ie disk_to_local_disk option. Chose the beginner's mode. The new HDD ie 500 GB one seems to work ok, but have I missed something here? Please guide me with your expertise. Any tips for future will be appreciated. Thanks a lot.

---

### Post by CharlesA on 2012-07-14
How long it takes to clone a device depends on how much data is on it. I haven't really used device-to-device cloning, but I thought they used dd, which does a bit-for-bit copy of everything, including freespace.

---

### Post by tech291083 on 2012-07-14
> **CharlesA said:**
> How long it takes to clone a device depends on how much data is on it. I haven't really used device-to-device cloning, but I thought they used dd, which does a bit-for-bit copy of everything, including freespace.

I though the same way as you have mentioned and it does make sense to me to an extent, but I need some assurance as to the average time taken by CloneZilla for device-device cloning under normal circumstances, thanks again.

Is there any other free, open source cloning software that I can use on my Fedora (or any other distro) pc? CloneZilla has been recommended to me by many, but let me get assured first.
Thanks.

There are so many to choose from as listed on this web page.

[http://en.wikipedia.org/wiki/List_of_disk_cloning_software](http://en.wikipedia.org/wiki/List_of_disk_cloning_software)

Hi,

Here is what my destination HDD looks like in a terminal.

```

[root@localhost john]# fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

Disk /dev/mapper/VolGroup-lv_swap: 5536 MB, 5536481280 bytes
255 heads, 63 sectors/track, 673 cylinders, total 10813440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/VolGroup-lv_swap doesn't contain a valid partition table

Disk /dev/mapper/VolGroup-lv_root: 49.3 GB, 49325015040 bytes
255 heads, 63 sectors/track, 5996 cylinders, total 96337920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/VolGroup-lv_root doesn't contain a valid partition table

Disk /dev/mapper/VolGroup-lv_home: 24.6 GB, 24628953088 bytes
255 heads, 63 sectors/track, 2994 cylinders, total 48103424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/VolGroup-lv_home doesn't contain a valid partition table
[root@localhost john]# 

```

The attached screenshot of the Disk Utility software shows things more clearly as far as I am concerned. I am happy that it shows the remaining space 420 GB as free space. 

Thanks.

---

