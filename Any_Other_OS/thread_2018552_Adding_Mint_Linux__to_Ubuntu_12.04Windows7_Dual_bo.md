---
title: "Adding Mint Linux  to Ubuntu 12.04/Windows7 Dual boot"
date: 2012-07-06
forum: Any Other OS
---

### Post by zuheyr on 2012-07-06
Hello,

I managed to install the Ubuntu 12.04/Windows7 after quite a struggle, mainly thanks to MorisseyJ's post about the b43 firmware...

I want to add, however, Mint Linux Cinamon to this couple but I do not want to destroy what I got real hard.

Would you please care to give your take on this. Thank you very much for reading. 

Regards, Zuheyr

---

### Post by oldfred on 2012-07-06
Moved to other OS.

What partitions do you have now and where is the space you want to use? Post gparted screenshot or fdisk output.

Also which boot loader do you want to be in charge or first on menu list? You can only have one grub in the MBR, but either should find all installs and update to let you boot all systems.

sudo fdisk -lu

df -H

---

### Post by Version Dependency on 2012-07-06
One thing you may want to try when dual booting multiple Ubuntu's (and Ubuntu derivatives) is making a partition for your home folder so it can be shared between both.

---

### Post by zuheyr on 2012-07-07
> **oldfred said:**
> Moved to other OS.

What partitions do you have now and where is the space you want to use? Post gparted screenshot or fdisk output.

Also which boot loader do you want to be in charge or first on menu list? You can only have one grub in the MBR, but either should find all installs and update to let you boot all systems.

sudo fdisk -lu

df -H
Thank you so very much!
This is the gparted image.
[http://ubuntuone.com/6t0yzhXoATkdY0qnPwk3BQ](http://ubuntuone.com/6t0yzhXoATkdY0qnPwk3BQ)

In the first disk I have Ubuntu 11.10 and Windows Vista, both 32.
In the 2nd hard disk, which replaced a recently crashed one, I have 3 primaries: Windows 7, 2 storages ntfs, and an extended which houses the Ubuntu. They are all 64.
I have a 680GB saved unallocated space in the extended partition that I intend to put the mint and the next ubuntu versions...
I installed Windows 7 first in the 2nd disk. Windows 7 found the Vista. Ubuntu 12.04 finds the Windows 7 (but not the Vista...). 
 
zuheyr@zuheyr-Inspiron-530s:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      144584       72261    6  FAT16
/dev/sda2          145408    21116927    10485760    7  HPFS/NTFS/exFAT
/dev/sda3   *    21125475   252541799   115708162+   7  HPFS/NTFS/exFAT
/dev/sda4       252541924   976768064   362113070+   5  Extended
/dev/sda5       959353605   976768064     8707230   82  Linux swap / Solaris
/dev/sda6       252541926   252814904      136489+  83  Linux
/dev/sda7       252817408   959352831   353267712   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x506f0275

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   524281855   262139904    7  HPFS/NTFS/exFAT
/dev/sdb2       524281856  1153427455   314572800    7  HPFS/NTFS/exFAT
/dev/sdb3      1153427456  1782573055   314572800    7  HPFS/NTFS/exFAT
/dev/sdb4      1782573056  3907026943  1062226944    5  Extended
/dev/sdb5      1782575104  1783623679      524288   83  Linux
/dev/sdb6      1783625728  1825568767    20971520   83  Linux
/dev/sdb7      1825570816  1850736639    12582912   82  Linux swap / Solaris
/dev/sdb8      1850738688  2479884287   314572800   83  Linux
------------------------------------------------------------------------------

And df -H

zuheyr@zuheyr-Inspiron-530s:~$ df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb6        22G  3.7G   17G  19% /
udev            2.1G  4.1k  2.1G   1% /dev
tmpfs           828M  902k  827M   1% /run
none            5.3M     0  5.3M   0% /run/lock
none            2.1G   82k  2.1G   1% /run/shm
/dev/sdb5       535M   74M  434M  15% /boot
/dev/sdb8       322G  5.0G  301G   2% /home


Great many thanks again, regards, Zuheyr

---

### Post by zuheyr on 2012-07-07
> **Version Dependency said:**
> One thing you may want to try when dual booting multiple Ubuntu's (and Ubuntu derivatives) is making a partition for your home folder so it can be shared between both.

Thank you! Yes this is certainly my intention.
In fact, I also intend to share the swap as well as I invested in a generous swap (please see the gparted image: 
[http://ubuntuone.com/6t0yzhXoATkdY0qnPwk3BQ](http://ubuntuone.com/6t0yzhXoATkdY0qnPwk3BQ)

Following a great article on swap I unfortunately cannot recall now and have no time ATM to search for again, I put 3 times the ram (4GB).

And I do not hibernate, so my research indicates sharing the swap will be ok. 

Many thanks, Zuheyr.

---

### Post by oldfred on 2012-07-07
With 4GB of RAM swap only needs to be 4GB if hibernating and even less unless planning to edit video, then your really want unlimited RAM anyway.

The old rule on swap being 2 times RAM was when RAM was 256K or 512K. Then with 2GB of RAM or more it became 1 times RAM. Some with over 4GB of RAM have no swap but it usually is better to have at least a little.

Windows combines all boot files from a second install into the first, so there is only one bootable Windows partition. Grub's os-prober then can only find one Windows to boot and then you have to choose which Windows to boot from the Windows menu. If you want to split the boot, you have to separately repair each Windows install so it has its own boot files.

---

### Post by Paddy Landau on 2012-07-07
I don't know the answer to your problem, but I do know that when I want to protect my investment in time (especially with Windows), I back up the entire hard drive. That way, if I make a real screw-up (or my kids put viruses onto Windows), I can just restore.

I use [CloneZilla]("http://www.clonezilla.org/") for this. It's not the most user-friendly system around, but it works. You can also try [Redo Backup]("http://redobackup.org/"), which is much more user-friendly.

---

### Post by zuheyr on 2012-07-07
> **oldfred said:**
> With 4GB of RAM swap only needs to be 4GB if hibernating and even less unless planning to edit video, then your really want unlimited RAM anyway.

The old rule on swap being 2 times RAM was when RAM was 256K or 512K. Then with 2GB of RAM or more it became 1 times RAM. Some with over 4GB of RAM have no swap but it usually is better to have at least a little.


Thank you. I tried to find the article I used and read a number of new ones now but you are right. I will reduce it to say 4.5GB max! 

On the other hand: 
I have added the Mint Linux variants sharing the same swap and the home partitions.  Please see the gparted image.

[http://ubuntuone.com/6GJIgo56FO2IDYdhitcUIC](http://ubuntuone.com/6GJIgo56FO2IDYdhitcUIC)

Just for the next newbie like myself.
I put the loaders in their /boot partitions and updated the Ubuntu grub after each install. All is fine (despite the same b43 firmware glitch). 

Regarding the Windows, yes, no problem, Windows 7 booter located the Vista. 

Thank you very much. Best regards, Zuheyr

---

### Post by zuheyr on 2012-07-07
> **Paddy Landau said:**
> I don't know the answer to your problem, but I do know that when I want to protect my investment in time (especially with Windows), I back up the entire hard drive. That way, if I make a real screw-up (or my kids put viruses onto Windows), I can just restore.

I use [CloneZilla]("http://www.clonezilla.org/") for this. It's not the most user-friendly system around, but it works. You can also try [Redo Backup]("http://redobackup.org/"), which is much more user-friendly.
Thank you! I did not know these tools. Much appreciated, particularly because I want to learn and making many more mistakes on the way... Thanks very much. Best regards, Zuheyr

---

### Post by oldfred on 2012-07-07
You should not need separate /boot for most desktop installs and you cannot share a /boot.

I do not like to share /home. Those that say you can share the partition are suggesting you use different user names so no settings conflict. But then the data is still in a different location. 

I prefer to create data partition(s) with multiple installs and just mount the data partition into each system. 

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by zuheyr on 2012-07-08
Yes, yes, about the /boot I know there are very elegant solutions with a separate boot partition but I did not have enough time to learn that yet... 

Regarding separate home, excellent references, great material to study, many thanks. I wanted to have the same user name to have the same email folders etc. 

I realized the possible conflictions but I will not be really actively using 3 distros equally intensively.  Just testing, but I like Unity. Mint looks great etc but Unity is the step forward and the way to go, IMHO. 

The whole setup is experimental and I already made one data partition available by mounting. In fact, In my case a more acute problem is to make one /opt be available to every distro which practically forced me to think along the lines of mount and link solutions you show. Very much appreciated, many thanks. 

Best regards, 

Zuheyr

---

