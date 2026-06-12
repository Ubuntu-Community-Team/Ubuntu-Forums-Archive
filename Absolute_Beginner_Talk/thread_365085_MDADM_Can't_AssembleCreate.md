---
title: "MDADM Can't Assemble/Create"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by mattdwilnew on 2007-02-19
Hey all,

I did something bad!
On my quest to try and get my MDADM raid to autorun on startup (refer here [http://www.ubuntuforums.org/showthread.php?t=355013](http://www.ubuntuforums.org/showthread.php?t=355013) ). I have stuffed something up and now i can't assemble the raid!
MDADM gives me a /dev/sda1: is too small: ok

When I started trying to install the RAID i installed DMRAID, and i was thinking that because there was two RAIDs trying to be setup that it was not running either of them! So i uninstalled the package (stupid i know now). Then when i went to create (sudo mdadm --create /dev/md0 --level=raid5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 --auto=yes) it gives me the following:
mdadm: /dev/sda1 is too small: 0K
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sun Feb 11 23:39:55 2007
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sun Feb 11 23:39:55 2007
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=1001023168K  mtime=Sun Feb 11 23:40:00 2007
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sun Feb 11 23:39:55 2007
mdadm: create aborted

All the volumes are coming up as Linux raid member.

I can't reinstall DMRAID it gives me:

mdadm: /dev/sda1 is too small: 0K
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sun Feb 11 23:39:55 2007
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sun Feb 11 23:39:55 2007
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=1001023168K  mtime=Sun Feb 11 23:40:00 2007
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sun Feb 11 23:39:55 2007
mdadm: create aborted

Please help! Its a work server and it needs to be up again tomorrow! Even if there is a way to force recover the drives and copy the data elsewhere.

---

