---
title: "System partition out of space"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by af20001 on 2007-02-09
Hi,

I installed 6.06 without much trouble. After the installation was complete, I ran GParted to create a separate partition to hold music files. Through the Disk Administration GUI I mounted a new music folder to the new partition. The problem I then had was that after restarting the machine, the mount point was lost, so the music folder (and all the files within it) was back under the main system partition. This then used up all the space on the system partition.

I have now fixed the problem by mounting the partition in the terminal, which has brought all the music files back into the right partition, but the system partition is still full. I have searched for copies of the music files in the system partition, but none are there.

Any ideas where I can look to see where all the space has gone? Is there a way to search for large files?

Thanks,
Andy.

---

### Post by alasdair.mccall on 2007-02-09
Hi,

I'm a bit confused. Was there extra space on you hard drive to create the partition or are you using more than one hard drives? If you post some system information I'd be glad to help. 

You can get disk and partition information by typing
> sudo fdisk -l
and mount information
> mount
and partition usage info
> df -h

Cheers,
Alasdair

FYI: I use the locate command to find files on my system. In the console type
> sudo updatedb
locate <file-name>


---

### Post by af20001 on 2007-02-09
No, it is a single disk (320Gb). It was a new disk with no other OS installed.

The main system partition is something like 12.5Gb, with the main file partition about 290Gb. The only extra program I have installed since the Ubuntu installation is Slimserver (which is fairly small).

I can't post more detailed info at the moment, as the box is a home machine (I'm at work now).

I'll try the locate command tonight.

---

### Post by af20001 on 2007-02-10
Hi,

This is what discus reports:

Mount           Total         Used         Free         Prcnt      Graph
/                  12.21 GB    11.48 GB   238.0 MB  94.0%   [*********-]
/sys             0 KB           0 KB         0 KB          0.0%   [----------]
/var/run        473.6 MB    124 KB      473.5 MB   0.0%   [----------]
/var/lock       473.6 MB     4 KB         473.6 MB   0.0%   [----------]
+oc/bus/usb 0 KB            0 KB         0 KB         0.0%    [----------]
/dev             473.6 MB     108 KB      473.5 MB   0.0%   [----------]
/dev/shm      473.6 MB     0 KB         473.6 MB   0.0%   [----------]
+6/volatile    473.6 MB     18.4 MB    455.2 MB   3.9%   [----------]
/music         259.03 GB    36.27 GB  209.60 GB 14.0%   [*---------]

As you can see, it reports that the system partition is virtually full. I can't see what is using up all the space, as when I run baobab, I can't see any folders that are using up all the space, and in fact baobab seems to report that there is only 2.2Gb used (38.5 Gb in total. of which 36.3 Gb is on the /music partition).. The /music folder is on its own partition.

Anyone got any ideas what is going on?

Thanks.

---

### Post by trace_on on 2007-02-27
I have the same problem and I see a lot of threads explaining a similar situation, but no answers... Did this problem get solved? What was the resolution?
It's driving me mad...

---

