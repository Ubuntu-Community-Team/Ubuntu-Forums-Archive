---
title: "Live CD Partition Question"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by rdp on 2007-03-13
Ok, heres my problem, I have no idea what I am doing.
Ok, heres my question, I get through the install portion of the live cd untill I get to the prepare disk space screen. It then asks, how do you want to partition this disk? I am given two choices; 1.erase entire disk or 2. manually edit partition table. Not wanting to erase everything I picked #2, which brings me to a screen which shows the existing partitions on my hard drive. I am only running XP but it looks to my untrained eye that I have three partitions. From there I select the largest partition to partition, which brings me to a screen titled; prepare mount points. It then goes on to say, select which partitions you want to use for your new installation and where you want to mount each of them. You must mount one partition on the root file system ("/"), and you must choose at least one partition for use as swap place.
Mount Point                                         Size                                        Partition
/media/sda1                                          55mb      partition1disc usb/scsI/sata1(primary)[sda1
/media/sda3                                          3gb       partition3disc usb/scsI/sata1(primary)[sda3]
/media/sda2                                        146gb      partition 2disc usb/scsI/sata1(primary)[sda2
Any body have any idea what I should do next ?
Thanks ahead of time for any help .

---

### Post by bernied on 2007-03-13
hmmm, maybe you should stop for a minute.
You may be about to wipe your windows partition - is this what you want?
If it is then just allow ubuntu to install itself on the whole disk.

If it is not what you want then you should do some research on dual-booting before you continue.

---

### Post by mikewhatever on 2007-03-13
Generally speaking, to create Ubuntu partitions (root, swap) you need free unallocated space. If there is non on the disk, one of the existing partitions must be resized to make unallocated space. I am not sure what's the USB stuff is in your case. Are you partitioning an external USB HDD? In order to resize/shrink a partition, free space must be available on it, and it must be defragmented to facilitate the process. It looks like sda2 is the only partition suited for resizing. 
Once you have the unallocated space, right clicking on it should present an option to create more partitions. Since you already have 3 primary ones, create extended/logical partitions for Ubuntu, root - about 10 BG, swap - about 0.5-1 GB. Then mount them as / and swap respectively.

---

