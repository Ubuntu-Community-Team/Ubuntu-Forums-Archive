---
title: "BIG partition problems"
date: 2008-01-14
forum: Apple Intel Users
---

### Post by tommy1987 on 2008-01-14
I have the following outputs in my term:
 
 blah:~ tom$ diskutil list /dev/disk1
 /dev/disk1
 #: TYPE NAME SIZE IDENTIFIER
 0: Apple_partition_scheme *111.5 Gi disk1
 1: Apple_partition_map 31.5 Ki disk1s1
 2: Apple_HFS tom 111.5 Gi disk1s2
 blah:~ tom$ diskutil list /dev/disk2
 /dev/disk2
 #: TYPE NAME SIZE IDENTIFIER
 0: Apple_partition_scheme *838.5 Mi disk2
 1: Apple_partition_map 31.5 Ki disk2s1
 2: Apple_HFS MacTeX-2007 838.4 Mi disk2s2
 blah:~ tom$ diskutil list /dev/disk3
 Could not find disk: /dev/disk3
 blah:~ tom$ diskutil list /dev/disk0
 /dev/disk0
 #: TYPE NAME SIZE IDENTIFIER
 0: GUID_partition_scheme *111.8 Gi disk0
 1: EFI 200.0 Mi disk0s1
 2: Apple_HFS Macintosh HD 85.9 Gi disk0s2
 3: Microsoft Basic Data BOOTCAMP 22.3 Gi disk0s3
 4: EFI 2.0 Gi disk0s4
 5: Linux Swap 160.8 Mi disk0s5
 
 However what confuses me is that I only have one physical disk (The HDD in the macbook which to the best of my knowledge is 120Gb).
 
 I need to discover what it is safe to delete, since I want to restore my macbook to a similar to original state. My only problem is I know messing around with partitions is dangerous and my system works fine so I don't want to mess anything up.
 
 I have bootcamp installed and put windows on but then I overwrote that partition with linux and have since put a 3rd party boot manager on my system which gives me the choice of OS/s when I startup my machine without holding down any keys.
 
 I tried to use bootcamp to free up the space but this gives an error since the partition has been modified when I installed Linux straight over Windows which I admit was a complete bodge job on my part. Now I basically want to free up the space and restore the whole thing to one drive with one partition.
 
 Somebody please help me :-s

---

### Post by cyberdork33 on 2008-01-14
boot up an Ubuntu Live CD and start the Partition editor. This will allow you to see all the partitions on each disk, and there will be a drop down menu with various found hard drives if there is more than one. It is very strange output that you have.

NOTE:, you can just use 'diskutil list' by itself, and it will list all the drives and the partitions found on the system. It looks as though something got confused somewhere...

also, please use the code tags to format the output from the terminal so that it is a bit more legible.

---

