---
title: "Correct way to add new drive in fstab"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by RTrev on 2007-10-19
When I did a fresh install of Gutsy yesterday, I decided to convert my two 500G data drives into a RAID-1 array.  Works fine, but I must have something wrong in fstab because, although the drive is mounted and works, I end up with an icon on the Gnome desktop.   I never saw that happen before unless a drive wasn't mounted via fstab.

Here is what my current fstab looks like, with my addition of the RAID-1 (md1) array at the bottom.  Can anyone see anything wrong with this?  And, any suggestions for a choice of options to use?  I'm the only user of the machine, so would like full access.  I found that I had to go in with sudo nautilus to set the protections to what I wanted.  It's okay now, but that icon on the desktop bugs me.  :)

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=dfd8b3c7-71d9-4555-86c9-db415b05472c /               ext3    defaults,noatime,nodiratime,errors=remount-ro 0       1
# /dev/sda1
UUID=d9ddd803-5698-47ce-8b00-61a48b80fef7 /boot           ext2    defaults        0       2
# /dev/sda2
UUID=f1d96d0d-b184-437e-8ee0-76040ceb82a4 none            swap    sw              0       0
# /dev/sdb1
UUID=50576ef7-3e92-44a1-abb2-5cfe14170761 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

# add the big RAID-1 array
# /dev/md1
UUID=33f2638c-f8da-4494-8337-be8b5d11f34e  /home/bob/Data  ext3  defaults,auto,exec,users,noatime,nodiratime 0 2

```

Thanks for any ideas.  I like to keep a nice,clean desktop, with the only icons ones which I've put there for a reason (current project, etc.)

Best,
Bob

---

### Post by nchase on 2007-10-19
I'm not an fstab expert...so this might not get at the root of the problem, but it may be a "quick fix" for you:

run gconf-editor

go to:

apps > nautilus > desktop 

if volumes_visible is checked, uncheck it.

---

### Post by RTrev on 2007-10-19
> **nchase said:**
> I'm not an fstab expert...so this might not get at the root of the problem, but it may be a "quick fix" for you:

run gconf-editor

go to:

apps > nautilus > desktop 

if volumes_visible is checked, uncheck it.

Thanks.. that removed the icon, but it also removed those of any CD or USB drive I might have plugged in.. and those I find handy to have.  But we're close!  :)

Never had this problem before, but then I never tried a RAID array other than of the system disks.  The two 500G drives were always mounted separately, and never showed up on the desktop.  Hmm.

---

### Post by Hospadar on 2007-10-19
It probably has to do with the raid array
I would bet for whatever reason gnome is picking up half of the raid drive as a new drive even though it's in raid.
I would bet there's no simple way to get rid of the icon as it seems like a little bug in the way the drive detection works.

---

### Post by RTrev on 2007-10-19
> **Hospadar said:**
> It probably has to do with the raid array
I would bet for whatever reason gnome is picking up half of the raid drive as a new drive even though it's in raid.
I would bet there's no simple way to get rid of the icon as it seems like a little bug in the way the drive detection works.

Oh well, not the end of the world.. and certainly not a high-priority item.  I'll just use nchase's suggestion, and live without the USB or CD/DVD icons.  

It's odd that my other two disks are also RAID and they don't display this problem.  They are RAID-0 as the system disk /dev/md0.  Maybe it's because I defined the RAID-1 drives during install, and chose to not mount them.  I wanted them mounted by myself, and not as, for example, /usr.  Perhaps that was my mistake.  Or perhaps it's a bug, as you say.  

Thanks for the feedback.

Bob

---

### Post by RTrev on 2007-10-20
I think I may have found the problem, but not the solution.

The UUID of the md array doesn't seem to be the same in mdadm as in vol_id, which shows as an old bug:

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/126499](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/126499)

```

bob@ub64:~$ sudo vol_id /dev/md1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=33f2638c-f8da-4494-8337-be8b5d11f34e
ID_FS_UUID_ENC=33f2638c-f8da-4494-8337-be8b5d11f34e
ID_FS_LABEL=Data
ID_FS_LABEL_ENC=Data
ID_FS_LABEL_SAFE=Data

```

```

bob@ub64:~$ sudo mdadm -D /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Thu Oct 18 16:59:59 2007
     Raid Level : raid1
     Array Size : 488383936 (465.76 GiB 500.11 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Oct 20 20:50:08 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 54caa3c2:c67fcfcc:fb9fc1bf:599daee4
         Events : 0.34

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1

```

That isn't right, is it?  Any suggestions how to fix it?

Thanks,
Bob

---

