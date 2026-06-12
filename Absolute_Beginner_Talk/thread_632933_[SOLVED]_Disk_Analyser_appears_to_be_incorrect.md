---
title: "[SOLVED] Disk Analyser appears to be incorrect"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by bobmac on 2007-12-06
Folks,

I have a 320Gb disk which I partitioned into 2. I installed windows on 1 partition and ubuntu on the other.

On the windows partition I can see that the total disk space is 160Gb or there abouts, however, when I try out the Disk Analyser option from the Applications | Accessories menu the Total File system capacity reads as 34.3 Gb with the Used as 2.9Gb and Available 31.4Gb.

Can anyone explain where the 130Gb has gone?

Bob

---

### Post by thelatinist on 2007-12-06
```
sudo sfdisk -l
```

Post the results here.

---

### Post by vikram on 2007-12-06
> **thelatinist said:**
> ```
sudo sfdisk -l
```Post the results here.

make that 

code]sudo fdisk -l[/code]

also suggest you post output of 

```
df -h 
```

---

### Post by thelatinist on 2007-12-06
> **vikram said:**
> make that 

code]sudo fdisk -l[/code]

also suggest you post output of 

```
df -h 
```

Good point about df -h.  As far as fdisk vs. sfdisk, they should work basically the same (sfdisk is scriptable fdisk).  I always use sfdisk because it shows empty primary partitions and also gives the number of cylinders. It's just a matter of preference.

---

### Post by vikram on 2007-12-06
never tried sfdisk now I have another tool to explore!

thanks !

---

### Post by jcarrete on 2007-12-06
Hello,

I some sort of a similar problem.  When I try _GParted_ I get one size and when I use _Disk Usage Analyzer_ I get a different one.

When I add up the sizes of the folders in that partition as shown by the _Disk Usage Analyzer_ it gives me less than 5.5 GB.  On the other hand, _GParted_ says that out of 39 GB only have 548 MB unused (*i.e.*, it says I am using 38.35 GB,  One of the two must be mistaken.  Quite likely is the _Disk Usage Analyzer_ as I am currently having issues as the system is now telling me the disk is 100% full but I do not know where the rest of the disk is.

At least if the output of the _Disk Usage Analyzer_ was correct I would know where the remaining 33.5 GB are.

Any help would be really appreciated.

P.S.: I have attached screen shots of both the _Disk Usage Analyzer_ and _GParted_.  Note that /home is an entirely different partition which seems to be reported correctly in both programs.

---

### Post by philinux on 2007-12-06
try the System Monitor - the last tab is file systems, i prefer this to all others.

---

### Post by jcarrete on 2007-12-06
I missed thin in my previous posts.  This is the output using ```
sudo sfdisk -l
```

```

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+   5098    5099-  40957686   83  Linux
/dev/sda2       5099    5736     638    5124735   82  Linux swap / Solaris
/dev/sda3       5737   38912   33176  266486220   83  Linux
/dev/sda4          0       -       0          0    0  Empty

```

Attached is the screen shot of the _System Monitor_.

---

### Post by philinux on 2007-12-06
According to the sysmon output your whole drive is linux. I.e. 300 gig approx and your / is showing 100% full nearly. :confused:


 root is showing as 38.4 gig
/home partition as 250.2 gig

approx 300 gig

---

### Post by jcarrete on 2007-12-06
Indeed, all my partitions are Linux.  My issue is not with a dual boot machine as the original post on this thread but it is with the _Disk Usage Analyzer_ which is mentioned as reporting an incorrect amount.

As you say, my root folder looks full but according to the _Disk Usage Analyzer_ I still have plenty of room.  So, where did the rest?  That is, there seem to be about 33.5 GB 'lost'.

Again, I would appreciate any help in recovering that portion as I am currently getting a disk full message which I am affraid may be symptom of something worse.

---

### Post by philinux on 2007-12-06
You never get the full manufacture quoted Gig or Meg. They count 1000 the computer counts 1024.

What on earth have you got in root - here's my sys mon.

As you can see root is only using 3.5 gig.

---

### Post by LowSky on 2007-12-06
a 300 Gigabyte hard drive is going to have 300000 Megabytes, when it really should have 307200 Megabytes. Thats missing about 7 Gigabytes, and because drive makers always exageate to begin with, you are most likely closer to 9 -15 Gigabytes in the hole. so when you buy a 300 Gigabyte drive your reallly buying 285-290 Gb

---

### Post by thelatinist on 2007-12-06
Whatever is taking up that space appears to be in the root folder itself.  Check to see what files are in there are in terminal by going to doing:

```
ls -al /
```

ls lists files and directories. -al makes it include hidden files and list details (like size, etc.).

If you can't figure out from that, paste the results here.

---

### Post by bobmac on 2007-12-06
Vikram and thelatinist

Folks, 

Here are my results:

~$ sudo sfdisk -l

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  10198   10199-  81923436    7  HPFS/NTFS
/dev/sda2      10199   19453    9255   74340787+   7  HPFS/NTFS
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda3      19454   24283    4830   38796975   83  Linux
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/sda4      24284   38912   14629  117507442+   5  Extended
/dev/sda5      38156+  38912     757-   6080571   82  Linux swap / Solaris
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)
/dev/sda6      29030+  33513    4484-  36017667   83  Linux

df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda8              35G  2.9G   30G   9% /
varrun               1014M  216K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   76K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile

/dev/sda7      37778+  38155     378-   3036253+  82  Linux swap / Solaris
/dev/sda8   *  24284+  28828    4545-  36507649+  83  Linux
/dev/sda9      28829+  29029     201-   1614501   82  Linux swap / Solaris

Perhaps you could give me a clue as to what all this means

Many thanks

Bob

---

### Post by thelatinist on 2007-12-07
First of all, you do not, as you thought, have your hard drive partitioned into two.  You have somehow managed to get your hard drive partitioned into NINE parts (eight partitions and one unpartitioned space).  I will try to explain it to you in simple terms:

Your hard drive consists of:

/dev/sda1 - 78.1 GB in a primary Windows partition formatted as NTFS
/dev/sda2 - 70.7 GB in a primary Windows partition formatted as NTFS
/dev/sda3 - 37.0 GB in a primary Linux partition Formatted as ext3
/dev/sda4 - 112.1 GB in an extended partition which is further divided into 5 smaller logical partitions and one unpartitioned space (since you can only create four primary partitions on a drive, all others have to be grouped into a larger 'extended' partition).  These are in physical order:
. . /dev/sda8 - 34.8 GB linux partition (this is the partition that is set as / on your system)
. . /dev/sda9 - 1.54 GB linux swap partition (this is your swap partition)
. . /dev/sda6 - 34.35 GB linux partition
. . /dev/sda7 - 2.90 GB linux swap partition
. . . . . . . . . . . . 32.68 GB Unpartitioned space
. . /dev/sda5 5.80 GB linux swap partition

If you add up sda1-sda4, you get over 297 GB, which is over 305 GB the way hard drive manufacturers measure (1GB=1,000,000KB).

I don't know how you got your system divided into so many partitions.  Perhaps you had two aborted installs of linux? In any case, now that you're in this mess your next question is probably  "Okay, so how do I fix it?"  Fortunately, it should be fairly easy to recover this space:

OPTION 1: Back up data, delete all Linux and extended partitions and reinstall Ubuntu

Advantages: Faster, Easier, Safer.
Disadvantages: You lose all your custom settings.

1) Backup all your data
2) Delete /dev/sda3 through /dev/sda9 (you can probably do this from the Ubuntu live CD)
3) Reinstall Ubuntu, letting it create new partitions for you in the free space.

OPTION 2: Using a GParted LiveCD to delete, move, and resize your partitions:

Advantages: Preserves all your custom settings.
Disadvantages: Slower, more difficult, more dangerous.

1. Backup all your data.  Although GParted is very good, messing with partitions is always dangerous.
2. Download and burn the iso, then boot into the GParted live CD.
3. The GParted window will open showing you a graphical representation of your hard drive and the partitions and free space that are on it.  It should be very close to what I showed you above.
4. Right-click on /dev/sda3 and choose delete from the context menu.
5. Right-click on /dev/sda4 and choose Resize/Move.  Adjust the partition to take up all the space you freed up in the last step.
3. Right-click on /dev/sda6, /dev/sda7, and /dev/sda5 and choose delete from the context menu.
6. Right-click on /dev/sda9 and choose Resize/Move.  Slide the partition all the way to the left, so that it is at the start of the partition.
7. Right-click on /dev/sda8 and choose Resize/Move.  Adjust the partition to take up all of the space freed up in the previous steps.
8. Click Apply.  This will take a long time to process (perhaps 1-2 hours).  During this time you will not be able to do anything on your computer.

When you are done, your hard drive should have four partitions:

78.1 GB NTFS
70.7 GB NTFS
112.1 GB extended
. . 110.56 GB ext3
. . 1.54 GB linux-swap

---

### Post by jcarrete on 2007-12-07
> **thelatinist said:**
> If you can't figure out from that, paste the results here.

Here are the results (note that I have listed the size in blocks and ordered them from largest to smallest).:

```

jcarrete@mycomputer:/$ ls -alsS
total 120
48 drwxr-xr-x   2 root root 49152 2007-03-06 07:33 lost+found
 0 drwxrwxrwt  17 root root 15940 2007-12-07 13:58 tmp
 0 drwxr-xr-x  12 root root 14440 2007-12-07 13:07 dev
 8 drwxr-xr-x 143 root root  8192 2007-12-07 13:31 etc
 8 drwxr-xr-x  17 root root  8192 2007-11-09 15:03 lib
 4 drwxr-xr-x  21 root root  4096 2007-11-09 14:55 .
 4 drwxr-xr-x  21 root root  4096 2007-11-09 14:55 ..
 4 drwxr-xr-x   2 root root  4096 2007-11-09 12:51 bin
 4 drwxr-xr-x   3 root root  4096 2007-11-09 15:00 boot
 4 drwxr-xr-x   6 root root  4096 2007-07-11 15:07 home
 4 drwxr-xr-x   2 root root  4096 2006-10-25 10:26 initrd
 4 drwxr-xr-x   7 root root  4096 2007-12-06 14:45 media
 4 drwxr-xr-x   5 root root  4096 2007-04-24 15:14 mnt
 4 drwxr-xr-x   2 root root  4096 2006-10-25 10:26 opt
 4 drwxr-xr-x  20 root root  4096 2007-11-22 11:50 root
 4 drwxr-xr-x   2 root root  4096 2007-11-22 09:35 sbin
 4 drwxr-xr-x   2 root root  4096 2006-10-25 10:26 srv
 4 drwxr-xr-x  12 root root  4096 2007-11-22 09:35 usr
 4 drwxr-xr-x  17 root root  4096 2007-11-09 12:40 var
 0 lrwxrwxrwx   1 root root    33 2007-11-09 14:55 initrd.img -> boot/initrd.img-2.6.22-14-generic
 0 lrwxrwxrwx   1 root root    33 2007-06-12 11:57 initrd.img.old -> boot/initrd.img-2.6.20-16-generic
 0 lrwxrwxrwx   1 root root    30 2007-11-09 14:55 vmlinuz -> boot/vmlinuz-2.6.22-14-generic
 0 lrwxrwxrwx   1 root root    30 2007-06-12 11:57 vmlinuz.old -> boot/vmlinuz-2.6.20-16-generic
 0 lrwxrwxrwx   1 root root    11 2007-03-06 07:36 cdrom -> media/cdrom
 0 dr-xr-xr-x 162 root root     0 2007-12-06 14:44 proc
 0 drwxr-xr-x  12 root root     0 2007-12-06 14:44 sys
```

From here it seems the lost+found is the one taking the largest amount.  of space.  I then go in that folder and repeat and this is what I get:

```
jcarrete@mycomputer:/lost+found$ ls -alsS
total 52
48 drwxr-xr-x  2 root root 49152 2007-03-06 07:33 .
 4 drwxr-xr-x 21 root root  4096 2007-11-09 14:55 ..

```

Any suggestions?

---

### Post by thelatinist on 2007-12-07
Okay, those were files that were saved during a system failure.  They aren't needed.  To remove them, try this:

```
sudo rm -rf /lost+found/*
```

Since this is the command that everyone warns you against following, let me also warn you: never do this unless you know what it's going to do.  I will explain what each element in this command does and why you want to use it in this case.

**sudo** - Because you want to delete files that are owned by the user 'root' you need to start with sudo to give yourself root permissions.
**rm** - remove files
**-r** - specifies that any files in subdirectories should be deleted
**-f** - forces the removal of files without prompting (you don't want to have to accept every file's deletion)
**/lost+found/*** - selects every file in the directory lost+found

Again, never just paste commands like this into your terminal unless you understand what they're supposed to do, and if someone suggests them and you don't understand *ask.*

---

### Post by jcarrete on 2007-12-07
Thanks.  I tried it but it seems that nothing changes.  I am not positive that the folder actually has (or had) any data whatsoever.

When I list the command ```
ls -alsS
``` I get the lost+found folder at the top but it does not really seem to have anything in it.

What would be the best way to get the exact size of each folder?  As mentioned on my earlier post, I tried _Disk Usage Analyzer_ but this one seems to provide erroneous information as compared to what is shown by either the system monitor or GParted.

The disk is so full now that I am afraid I will not be able to perform too many tasks now before it becomes unstable.  Is there any standard location of temporary files that I can just go and delete? (cache files, etc.)

Note that I get a message: 'Unable to copy the user's Xauthorization file.' now every time I try to run things like GParted or even worse synaptic (I am trying to delete some of the packages while I figure out a solution).

---

### Post by thelatinist on 2007-12-07
> **jcarrete said:**
> Thanks.  I tried it but it seems that nothing changes.  I am not positive that the folder actually has (or had) any data whatsoever.

When I list the command ```
ls -alsS
``` I get the lost+found folder at the top but it does not really seem to have anything in it.

Something is taking up that space.  Try this:

```
sudo rm -Rf lost+found
sudo mkdir lost+found
```

The first command will delete the entire folder 'lost+found' and anything in it.  The second command will recreate the folder.

---

### Post by jcarrete on 2007-12-07
> **thelatinist said:**
> Something is taking up that space.

Eureka... I found the issue.  First of all, it seems that the lost+found folder was OK.  I really do not know why it shows as large in size but it is not as it is empty so what 'size' means when doing ls -al or ls -alsS is still a mystery to me.

To find the root of my problem I decided to list all of the contents of the root folder and order them from the smallest to the largest using

```
sudo find / -type f -printf "%k %p\n" | sort -n
```

This lists all regular files (**-type f**), and prints their size in kilobytes (**%k**) and file name with their corresponding folders (**%p**) each on a new line (**\n**).  It then sorts them numerically. 

Since this produced a file that was too big it would not work (as my hard drive was already full).  So one by one I listed the contents of all folders (except for /home as it is in a different partition).  This way I was able to find that there were many _**huge**_ files in: **/media/LACIE/backup**.  I then deleted all of them and then after a reboot it all worked fine.

Although this fixed my problem it is the sign of something really strange.  LACIE is an external USB drive which I use for automatic backups so in theory this issues would have never filled my base folder (*i.e.*, /dev/sda1 partition in the internal hard drive).   Digging a bit further I relised that there were actually two folders under /media with similar names: one **LACIE** and the other **LACIE_**.  I imagine that the external was mounted as **/media/LACIE_** after some restart or after unplugging it and plugging it back in.  Since the backup software I use (_Simple Backup_) did not find the original **/media/LACIE/backup** folder (it would have been **/media/LACIE_/backup** due to the new mount name) it decided to create it.  As a result, all my daily incremental and monthly full backups were being saved on the /dev/sda1 partition on my internal hard drive.

In brief, I believe both _Disk Usage Analyzer_ and _Simple Backup_ both have issues.  The first failed to list the usage inside it sub-folders and the second decided to create a folder where it shouldn't have.  I am not sure it this is to be reported somewhere.

Thanks for the help.

---

### Post by bobmac on 2007-12-08
thelatinist,

Many thanks for the information and explanation. I'm not sure how I managed to get into such a pickle.

It seems that what I've somehow managed to do is when I thought I was upgrading from  version 7.04 to version 7.10 I've done something else instead. 

I got a bit confused when I started the installation procedure from the live CD and got to the bit about partitioning. The text at that point seemed to be telling me that it was going to delete everything before it could install the new version. I suspect that this is were I went wrong.

Since I'm pretty new to all this linux stuff I'll probably take your advice and delete everything and start again.

Anyhow, again, many thanks for your help

Bob

---

### Post by thelatinist on 2007-12-08
I'm glad I could help.  Don't forget to mark your thread [Solved] using the threat tools.

By the way, I love the Latin quote in your signature. ;-)

---

