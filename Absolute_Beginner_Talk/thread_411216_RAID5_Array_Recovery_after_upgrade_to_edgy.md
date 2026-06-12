---
title: "RAID5 Array Recovery after upgrade to edgy"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by hazmatt on 2007-04-16
I need to know if I can fix this or if I should bite the bullet and start reloading my dvd backups.  Again.  I have 90-95% backed up, but it's about 1.6 TB of data on hundreds of DVDs, so you know how painful reloading is.

I have 6 400 GB SATA drives on a RAID5 array mounted to /home.  System is 6.06 (dapper) Server kernel 2.6.15 with mdadm (don't know the version).  I recently installed a new motherboard with more on-board SATA connectors as I was also planning to start adding more drives.  The plan was to add a 3 bay enclosure that can hold 5 drives and setup 3 500 GB drives in another RAID5 array now and expand to 5 later.  There were two issues with this, both of which I realize now could probably have been resolved if I had simply taken the time to learn how to compile a new kernel.  The network drivers weren't loaded when it booted (two on the board), so I had to use a card, and I remember reading that I would need a newer kernel than was available in the apt repository for ubuntu 6.06 to expand an array.

So, instead of compiling a new kernel, I decided to do a fresh install of 6.10 (edgy) server.  During install, there was a some problem with DHCP, and it took me back to the menu.  I got it sorted out but didn't realize until it finished that it managed to skip several sections of the installation, including user setup.  With no login, I ran the recovery.  When it finished, it looked ok.  mdadm showed the device as /dev/md0(what it had been), and it mounted fine.  If everything else had been fine, it would have been what I wanted, however, the install had missed other stuff besides user accounts, for example, not only were there no apt sources configured, there were no man pages installed.

Another reinstall, all the way through this time.  mdadm didn't set it up correctly this time.  Here is the current status.

> # mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Apr 15 19:41:18 2007
     Raid Level : raid5
     Array Size : 1953556480 (1863.06 GiB 2000.44 GB)
    Device Size : 390711296 (372.61 GiB 400.09 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Apr 16 02:17:39 2007
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 9db5f426:b7ce1681:eb04cbd7:2b95de32
         Events : 0.2

    Number   Major   Minor   RaidDevice State
       0       8       64        0      active sync   /dev/sde
       1       8       96        1      active sync   /dev/sdg
       2       8       80        2      active sync   /dev/sdf
       3       8       48        3      active sync   /dev/sdd
       4       8      128        4      active sync   /dev/sdi
       5       8      112        5      active sync   /dev/sdh

> Disk /dev/md0: 2000.4 GB, 2000441835520 bytes
255 heads, 63 sectors/track, 243206 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       48641   390708801   fd  Linux raid autodetect


The only other thing is that last night, it showed it as degraded and resyncing one drive, and it finished the resync.  What should my next step be?

---

