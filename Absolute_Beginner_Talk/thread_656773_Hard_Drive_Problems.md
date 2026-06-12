---
title: "Hard Drive Problems"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by pastyear on 2008-01-02
I just recently installed ubuntu so that I could learn more about it. I wanted to keep Windows intact therefore, I decided to install ubuntu on a separate external hard drive. I set the partitioned space to be 50 gb, however after the installation I can now only access those 50gb of my 500 gb hard drive, even in windows. I am very new to this OS so I really have no idea how to fix this. I was wondering if anyone out there could help me fix this problem, I also wanted to be able to use the hard drive in windows to store other data. Here is some common info I saw other people post:

chris@chris-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        6903    55400152+   7  HPFS/NTFS
/dev/sda3            6904        7295     3148740   db  CP/M / CTOS / ...

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ba163

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6657    53472321    7  HPFS/NTFS
/dev/sdb2   *        6658       60234   430357252+  83  Linux
/dev/sdb3           60235       60801     4554427+   5  Extended
/dev/sdb5           60235       60801     4554396   82  Linux swap / Solaris

chris@chris-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=3d703f5e-21ed-49a2-8839-6948cad4afc3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=d1dc4487-5cdf-467f-a21d-a4148d621aa7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Thanks for any help

---

### Post by jken146 on 2008-01-02
> **pastyear said:**
> 
```

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1        6657    53472321    7  HPFS/NTFS**
/dev/sdb2   *        6658       60234   430357252+  83  Linux
/dev/sdb3           60235       60801     4554427+   5  Extended
/dev/sdb5           60235       60801     4554396   82  Linux swap / Solaris
```


It looks like you've got an NTFS partition on this external hard disk too.  Could you post the output of this please:  ```
df -h
```

---

### Post by pastyear on 2008-01-02
chris@chris-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             404G  2.1G  382G   1% /
varrun                760M   96K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
udev                  760M   96K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   34M  726M   5% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1              51G  9.1G   42G  18% /media/FreeAgent Drive

---

### Post by logos34 on 2008-01-02
It looks to me like maybe you got things backwards--when you did the (guided?) install the slider was indicating that the ubuntu partition would take up all but 50 GB of disk space (and that about how big the ntfs partition is)...Root as you can see from fdisk takes up almost all the disk, with a small swap at the end.

EDIT: yep, your last post proves it.  Windows can only see the ntfs partition (you'll need fs-driver to see the ext3)

---

### Post by jken146 on 2008-01-02
> **pastyear said:**
> ```
chris@chris-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             404G  2.1G  382G   1% /
varrun                760M   96K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
udev                  760M   96K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   34M  726M   5% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1              51G  9.1G   42G  18% /media/FreeAgent Drive
```

sdb1 is the NTFS partition that is 51G in size.  You'll be able to see this in both Windows and Ubuntu no problem.

sdb2 is the ext3 partition where Ubuntu is installed.  It is 404G in size.

If you want to access your ext3 partition from windows, check out [http://fs-driver.org](http://fs-driver.org).  Be aware that Windows will not respect your file permissions!

---

### Post by pastyear on 2008-01-02
Thanks for all your help! Yeah, my installation was not guided, I had trouble finding an installation guide and just went for it. But is there a way that I could re-install ubuntu to fix this problem or perhaps just reformat the hard drive again and install it over again?

---

### Post by logos34 on 2008-01-02
> **pastyear said:**
> Thanks for all your help! Yeah, my installation was not guided, I had trouble finding an installation guide and just went for it. But is there a way that I could re-install ubuntu to fix this problem or perhaps just reformat the hard drive again and install it over again?

Yes, you could reinstall.  Use Gparted on the live cd to delete sdb2 and the extended with swap. (System>admin>gnome partition editor).  Make sure to first disable automounting of hot-plugged devices in System>prefs>removable drives and media.

Or do manual partition again and delete the ubuntu partitions there.  (Don't check the 'format' box for sdb1 though--it looks like you have ~9 gb of stuff on it).  Then create new / and /swap.

---

### Post by tgalati4 on 2008-01-03
Perhaps Ubuntu is telling you something.  You might want to leave it for a while.  When Windows balls itself up in a few months, you will only lose the 50 GB partition.  Meanwhile Ubuntu will keep rolling along.

---

### Post by bwtranch on 2008-01-03
I always like saying this when anyone is willing to listen. Dual boot systems are no good. Only one queenie in the house. I don't care if it's an outhouse. Dual boot systems are inherently buggy. They use up valuable HDD space for no good reason. Causing people to devote valuable time and effort to maintain two (or more) OS's on the same machine. Computers are cheap these days and it would behoove a person to get another. I know I'll probably catch some flack But, I'm right on this one.

---

### Post by logos34 on 2008-01-03
> **bwtranch said:**
> I always like saying this when anyone is willing to listen. Dual boot systems are no good. Only one queenie in the house. I don't care if it's an outhouse. Dual boot systems are inherently buggy. They use up valuable HDD space for no good reason. Causing people to devote valuable time and effort to maintain two (or more) OS's on the same machine. Computers are cheap these days and it would behoove a person to get another. I know I'll probably catch some flack But, I'm right on this one.

Linux and XP coexist just fine together.  If you know what you're doing.  I haven't had any problems dual-booting on a single disk.  Separate computers?  That's a little extreme.  I might grant you separate hard drives (which is nice insofar as each OS has the disk to itself along with it's own bootloader, hence system redundancy), but not everyone has a second drive even.  You're overlooking the fact that some people need windows for work, or they're gamers, and Wine or running windows in vmware just won't cut it.  Computers are definitely getting cheaper, but then laptops have become all-in-one computing solutions these days, and if one wants to run linux without messing up XP or Vista installed on internal disk, it's easy to boot it from a usb. (well, most of the time, that is!)

---

### Post by tgalati4 on 2008-01-05
I've got a machine with Windows on one disk drive, and 4 Linux distros on a second drive.  It's possible for them to coexist and yes, it does require some work to maintain them.  The advantage is you can try 4 different distros and see what you like and dislike between them.  I only use Windows to load music on my Sony NW E505 player.  There's a linux driver in the works but its not ready yet.

Putting Linux on the same disk as Windows is a risk because Windows tends to ball itself up frequently and reinstalling Windows can wipe out the Linux parition (and your data) if you are not careful.  Of course the opposite can happen as well, especially if you are not sure of what you are doing.

---

