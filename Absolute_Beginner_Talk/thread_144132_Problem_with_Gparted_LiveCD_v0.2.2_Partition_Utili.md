---
title: "Problem with Gparted LiveCD v0.2.2 Partition Utility"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-13
Hello All !!!

I have the following problems with "gparted" from the "Gparted LiveCD v0.2.2 Partition Utility":

The program "gparted":

1. Can NOT resize a Hard Drive's Partition.
    Specifically the Ubuntu (OS) one.

2. Can Delete & Resize a Partition to a smaller Partition Size, but can NOT merge 
    separate unallocated (free) spaces.

    Example:

                  Partition 1:      | Partition 2:      | Partition 3:      | Partition 4:

1. Before:  20GB (OS)        | 20GB (EXT3)    | 40GB (EXT3)

2. Then:     20GB (OS)       | 20GB (Freed)   | 40 (Freed)

3. Final:     20GB (OS)        | 10GB (EXT3)    | 10GB (Freed)   | 40GB (Freed)


_Question 1_:
When I try to resize the first 20GB Partition to 15GB, I get an error...
I checked that my stuff take only 3GB of space, so it is NOT a space related issue here...
Do you get the same results? or is it a problem I encounter only?

_Question 2_:
Why on step 2 (above), the last 2 Partitions, when "Freed" (turned to empty or unallocated spaces), do not MERGE into 1 unallocated Partition?
And it gets even worse...

a. If I want to change the 20GB "Freed" Partition in step 2 (above), to (e.g.) 30GB 
    in step 3 (above), I am NOT permitted to....?

b. If the last 2 "Freed" Partitions could merge, I could (e.g.) create a Partition size 
    of 50GB, but now I am (again) NOT permitted...

Basically,  I am FORCED to have a 2nd Partition smaller than 20GB size...(NOT bigger)... && a 3rd Partition smaller than 40GB...
Finally, when I get to step 3, _AGAIN_: the last 2 (Freed) Partitions can NOT merge!!!

_Question 3_:
Is this how "gparted" is supposed to work?
... cause I downloaded the ".deb" file from Synaptic, installed it & running it from within Ubuntu, I get the SAME results...

And "qparted" works the same way too !!!


What is wrong?

Is there some other Partiitioning Program I should try out?


Thanks.

---

### Post by AtinLango on 2006-03-13
> Question 1:
When I try to resize the first 20GB Partition to 15GB, I get an error...
I checked that my stuff take only 3GB of space, so it is NOT a space related issue here...
Do you get the same results? or is it a problem I encounter only?


Make sure the partition is well defragged. Then try again.

---

### Post by dvarsam on 2006-03-14
But ALL the partitions are Linux ones...

Do Linux Partitions have to be Defragged?

_My case_:

1. Before: 20GB (OS) | 20GB (EXT3) | 40GB (EXT3)

At the same time, in the above, the last 2 partitions were Formatted but empty...
I had not copied, not even a single bit of data...

And only the first partition contains the Ubuntu OS...
You mean I have to "defrag" the Ubuntu Partition?

and ANY Linux partition before I start using it?

Thanks.

---

### Post by syg00 on 2006-03-14
[QUOTE=dvarsam]_Question 1_:
When I try to resize the first 20GB Partition to 15GB, I get an error...[/quote]Pointless asking questions like this if you don't provide the error message.> _Question 2_:
Why on step 2 (above), the last 2 Partitions, when "Freed" (turned to empty or unallocated spaces), do not MERGE into 1 unallocated Partition?Apparently the space is neither empty _nor_ unallocated.
I would guess you still have the space allocated to partitions - which are not empty even if you consider them unused.
Delete the partitions.> _Question 3_:
Is this how "gparted" is supposed to work?Probably.
Before you do anything, issue the following from a terminal session, and post the result here:```
fdisk -l
```(that's ell, as in list).

---

### Post by dvarsam on 2006-03-14
Hello & Thanks for your reply !

_"fdisk -l" Output_:

root@ubuntu:~# fdisk -l

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2951    23703876    7  HPFS/NTFS
/dev/hdc2            2952        4865    15374205    f  W95 Ext'd (LBA)
/dev/hdc5            2952        4865    15374173+  83  Linux

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433        4864    19535040   83  Linux
/dev/sda3            6080       10011    31583790    f  W95 Ext'd (LBA)
/dev/sda4   *        4865        6079     9759487+  83  Linux
/dev/sda5            6080       10011    31583758+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10416    83666488+   7  HPFS/NTFS
/dev/sdb2           10417       14593    33551752+   f  W95 Ext'd (LBA)
/dev/sdb5           10417       14593    33551721    b  W95 FAT32


The "Disk /dev/sda: 82.3 GB", is the one I would like to work on...

/dev/sda1               1        -> Ubuntu OS Partition (currently running)
/dev/sda2            2433     -> Empty EXT3 Partition (no data)
/dev/sda3            6080     -> f  W95 Ext'd (LBA) - (do not know)
/dev/sda4   *        4865    -> Suse OS Partition (Just experimenting - no data)
/dev/sda5            6080     -> Empty EXT3 Partition (no data - was once formatted from WinXP to a FAT32 Partition & changed with "gparted" to EXT3)

If you want me, I can erase the Partitions from 2-5 but they do NOT merge into 1 unallocated space...

(is it because "sda 5" was formatted from Windoze as FAT32?)
(I only did this because I wanted to save data, to be available at Windows too!)


Thanks.

---

### Post by syg00 on 2006-03-14
[QUOTE=dvarsam]
The "Disk /dev/sda: 82.3 GB", is the one I would like to work on...

/dev/sda1               1        -> Ubuntu OS Partition (currently running)
/dev/sda2            2433     -> Empty EXT3 Partition (no data)
/dev/sda3            6080     -> f  W95 Ext'd (LBA) - (do not know)
/dev/sda4   *        4865    -> Suse OS Partition (Just experimenting - no data)
/dev/sda5            6080     -> Empty EXT3 Partition (no data - was once formatted from WinXP to a FAT32 Partition & changed with "gparted" to EXT3)
[/quote]That configuration is a little messy (hence the "not in disk order" message) - no big deal. The fact that partitions show up in the list confirms the space is not free (nor unallocated). What you think of as "FREE" is merely unused (by you).> If you want me, I can erase the Partitions from 2-5 but they do NOT merge into 1 unallocated space...Probably a misunderstanding - I don't use the GUI front-ends, so I don't know what terminology gparted uses. If "erase" means merely deleting the data, nothing changes in this context. If it means "delete the partiton(s)", the (free) space certainly _should_ consolidate.
Do the erase and then post the "fdisk -l" for /dev/sda; that'll give us a better idea of what is actually happening.

---

### Post by dvarsam on 2006-03-14
Ok, sorry for the wrong "terminology" here.

Through the "gparted" program I selected "Delete" (to be specific) & deleted ALL the remaining partitions after Partition 1 (Partition 1 is the Ubuntu OS - do NOT ask me to delete this one...).

_Now my "fdisk -l" looks like_:

root@ubuntu:~# fdisk -l

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2951    23703876    7  HPFS/NTFS
/dev/hdc2            2952        4865    15374205    f  W95 Ext'd (LBA)
/dev/hdc5            2952        4865    15374173+  83  Linux

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda3            6080       10011    31583790    f  W95 Ext'd (LBA)

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10416    83666488+   7  HPFS/NTFS
/dev/sdb2           10417       14593    33551752+   f  W95 Ext'd (LBA)
/dev/sdb5           10417       14593    33551721    b  W95 FAT32


IF I use the "fdisk -l", ALL look OK:

1. /dev/sda1            -> Ubuntu Linux OS
2. /dev/sda3            -> Unallocated (Free) Space  f  W95 Ext'd (LBA)


BUT, if I view the above through the "Gparted" program, I see the following:

1. /dev/sda1            -> Ubuntu Linux OS                   (seems OK)
2.                             -> Unallocated 28,608                (<- This is the Problem)
3. /dev/sda3            -> Extended (LBA) 30,844         (<- This is the Problem)
4.                             -> Unallocated 30,844               (<- This is the Problem)

Basically 2-4 should show up as ONE "Unallocated" (Free) space...

Note:
3 & 4 show the SAME Partition "space" (or whatever you want to call it)... 

What is wrong?

Thanks.

P.S.> I wish I could post a Snapshot, but I do NOT know how to do this...

---

### Post by syg00 on 2006-03-14
Ahhhh   .....   **now** we're getting somewhere.
Believe it or not  ...:twisted: :twisted: 

O.K., as you observed, /dev/sda3 is the problem. From what you have described, this is not your problem, but a limitation in gparted. (feeling better now ???.  :p )
/dev/sda3 is an extended partition - it is merely a means of "containing" logical partitions. As such, you cannot directly use it to hold data, but it exists to allow you to create logical partitions. The space within an extended is deemed as different (separate if you like) to the space not in the extended (which is used for "primary" partitions like /dev/sda1 and what was /dev/sda2 and 4).
When you delete sda3, all the space will become available as one block. As I said,I don't know how to do that using gparted, but is easy with the CLI - fdisk or cfdisk.
cfdisk might be best - "cfdisk /dev/sda" will give you a curses display, use the down arrow to highlight sda3, and the side arrows to navigate the commands at the bottom of the screen. You need to delete sda3, then write the partition table back to disk, then quit.
Then reboot to pick up the changes.

_Be careful_ - your data, your decision. I find it's pretty straigh-forward though.

---

### Post by dvarsam on 2006-03-14
Thanks for your help man!!!

But when I decided to "delete" all the partitions after Partition 1 (my Ubuntu OS), so that I could get help from you, I did not think that my Grub would get destroyed....

..... you see, in Partition 3 I had installed as I said the Suse 10 Evaluation DVD....

..... and whenever I would boot my PC, a menu would then ask me if I want to boot from:

1. Suse
2. Ubuntu.

Now that I deleted the Suse, ... i can not boot man....

I managed to Boot from a Knoppix LiveCD (cause I currently do not have the Ubuntu LiveCD)...


My "/boot/grub/menu.lst file" looks like this:

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

Can somebody tell me what do I have to change to be able to Boot, like before, in my Ubuntu?


Thanks.

---

