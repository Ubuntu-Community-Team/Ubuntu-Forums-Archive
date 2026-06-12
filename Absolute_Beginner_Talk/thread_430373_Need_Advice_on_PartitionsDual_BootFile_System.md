---
title: "Need Advice on Partitions/Dual Boot/File System"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Chris S. on 2007-05-02
Hi.

I've absorbed quite a bit of information on Ubuntu and install procedures.  I think I've read through the entire psychocats site ([http://www.psychocats.net/ubuntu/)](http://www.psychocats.net/ubuntu/)), and a few other resources as well.  There's a long story as to why I've actually been studying all this material so much instead of actually jumping in (trust me, I would have long ago if I could).  To the point, I know basically what to do, I just need to make sure the following idea is going to work okay.

I want a Windows/Ubuntu dual-boot set up.  My idea is to format my hard drive (I need a *clean* start, so I'll actually get started on this after a few days of backup).  I'm going to install Windows XP Pro and SP2 without any extra partitions.  Then I'll install Ubuntu 7.04, and use the partition program during install (GParted or something?) to resize the Windows partition and make some new ones.  This is where I really need help, because this choice may have later repercussions.

I have a ~40 GB hard drive, so I was thinking of four partitions: 10 GB for Windows, 10 GB for Ubuntu, 1 GB swap, and the rest for /home and shared data.  The Windows partition will be NTFS, and everything else EXT3.  This last partition I was *hoping* to use for personal files from both OS's and also as a place for Windows programs to reside.  My disk usage is pretty fluid (vacillating between data files and installed programs) so I need a single partition that both OS's can read/write to *without issues*.


Some questions:
- Does anything jump out as wrong or something that's going to cause me headaches later?
- Is there enough space in the OS partitions for things to run smoothly?
- psychocats mentions "FS-Drive" for getting Windows to read/write from the EXT2/EXT3 filesystem.  Is this a good option for using that /home, shared partition as a place for files *and* Windows programs?  Are there other, possibly better options to do this?
- Any other advice, for instance, something I've overlooked?

I don't expect to get this right on the first try, but the more I know now, the less problems I face in the future.

---

### Post by renzokuken on 2007-05-02
i wouldnt recommend using the /home partition for windows programs, you may accidentally delete a file or something while in linux rendering the windows progs useless.

also, windows ability to read/write ntfs is not great. if you are going to have a shared partition i would recommend fat32. both OSes can read and write fat32 with no problems.

my recommendation would be the follwing

10gb    NTFS     windows and windows Progs
10gb    ext3      ubuntu
1gb      swap
19gb    fat32     /home or file storage for both win and *nix

just a recommendation though, i'm sure someone else could suggest something better

---

### Post by carl0ski on 2007-05-02
> **renzokuken said:**
> i wouldnt recommend using the /home partition for windows programs, you may accidentally delete a file or something while in linux rendering the windows progs useless.

also, windows ability to read/write ntfs is not great. if you are going to have a shared partition i would recommend fat32. both OSes can read and write fat32 with no problems.

my recommendation would be the follwing

10gb    NTFS     windows and windows Progs
10gb    ext3      ubuntu
1gb      swap
19gb    fat32     /home or file storage for both win and *nix

just a recommendation though, i'm sure someone else could suggest something better

I disagree

Fat32 is a terribly unreliable file system to use. and a very outdated decision
Ext3 is by far a superior choice.

my recommendation would be the following

10gb    NTFS     windows and windows Progs
10gb    ext3      ubuntu
1gb      swap
19gb    ext3     /home or file storage for both win and *nix


i have used ext2ifs for nearly a year with no problems at all. 
Once installed in windows under the control panel you'll fine IFS Drives Icon
From here you can choose a drive letter for your ext3 drives (all of them)
You can even safely use window Defragmenter
(which by the way doesn't find any fragmentation unless you torrent a bit)

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

### Post by renzokuken on 2007-05-02
much better suggestion....go with carl0ski

---

### Post by Chris S. on 2007-05-02
I had thought about the problems of using /home for programs, and I agree it's probably not a wise choice.  The thing is, 10 GB is not enough to fit everything I might need for Windows, but I don't want to eat up that shared space, because I'm sure I'll be needing it too.  At one time, I might need to use more space for programs, and another time I'd need more space for file storage, hence the idea of a single place to put everything.

Instead, if I use your ideas of leaving the Windows programs  in the NTFS partition, could I resize the partitions as my needs change?  Is that possible without formatting or damaging the data in that partition?

---

### Post by Shazaam on 2007-05-02
Chris S....
Is this a laptop or a destop? If it's a desktop can you add another hard drive? With the prices for harddrives these days being so cheap dual booting with 2 drives would be a better solution IMHO. Others may disagree with me on this. One drive for Windows and another for Linux. That way if your Linux install go toes up it usually wont take Windows with it depending on where you put your bootloader. With all of my experimenting I have managed to trash a few Linux installs but I haven't damaged Windows enough that a "fixmbr" wasn't able to fix it. 

fdisk -l
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38757   311315571    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1019     8185086   83  Linux
/dev/hda2            1020        9624    69119662+   5  Extended
/dev/hda5            1020        1528     4088511   82  Linux swap / Solaris
/dev/hda6            1529        3460    15518758+  83  Linux
/dev/hda7            3461        6023    20587266   83  Linux
/dev/hda8            6024        9624    28925001   83  Linux

This is WinXp on sda, Mandriva, Mepis, and Ubuntu on hda. For you the size of the drives wont matter. I dont have a shared /home (not brave enough yet) so your setup would be different. The only problems I have encountered were ones that have been self-inflicted :)

---

### Post by Chris S. on 2007-05-03
I'm on a laptop, but I was thinking of eventually getting an external hard drive for it.  It's way down on my list of computer repairs/upgrades, but it would null all of my concerns.  I'd probably leave Windows and Linux on the internal drive, with some shared space, but I'd probably use the second/external drive entirely for shared space.

---

### Post by msandersen on 2007-05-06
Why 10Gb for Ubuntu when you Home is on a separate partition? 5-6Gb should be plenty with room to grow. Also, the swap space needed depends on how much RAM you have, or intedn getting. General rule: Swap = 1 - 1.5 times the RAM. Personally, I use something in-between, nothing too mathematical, but maybe 1.2 times.

One thing to conserve space in the System is to have Synaptic clean the cache when it quits, else it keeps all the packages it downloads. Same as "apt-get clean'.

ext2IFS is a great driver, I've used it a while along with the NTFS-3G driver on Linux for the other way. The former is about to be updated to 1.11, but seems more like a 2.0, with full Vista and 64-bit support.

@Renzokuken:
> also, windows ability to read/write ntfs is not great. :D That's funny! I assume it was meant to be...
Definitely stay away from Fat32.

---

