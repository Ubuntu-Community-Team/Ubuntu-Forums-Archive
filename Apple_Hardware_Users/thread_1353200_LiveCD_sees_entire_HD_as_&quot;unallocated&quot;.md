---
title: "LiveCD sees entire HD as &quot;unallocated&quot;"
date: 2009-12-12
forum: Apple Hardware Users
---

### Post by Praxicoide on 2009-12-12
Hi, I'm trying to install Ubuntu 9.10 in an iBook G4. The iBook already has 9.04 installed on it, and boots fine, but for some reason freezes after some minutes.

I'm trying to update to 9.10, but having bad experiences with updates, I'm doing a fresh install.

I can't install, however, because according to GParted, the entire hard drive is "unallocated", and shows it blank. 

Booting off from the HD shows me /etc/fstab as it should be, with a /, /home and swap partition (there's a NewWorld partition in there too, but it's not shown on fstab).

Any clues as to why this happens and how I can make GParted read the HD correctly?

EDIT: I just installed GParted into the existing installation, and it also shows me the entire HD (the one it is running off!) as blank.

EDIT2: I just realized that the terminal gives me this warning for GParted: "The partition table doesn't have an entry in the partition table!"

---

### Post by Praxicoide on 2010-01-06
Here's /etc/fstab. Everything seems normal...

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/hda4 during installation
UUID=1cf4c466-edd2-4c0e-b4d2-21f89e0358f0 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/hda2 during installation
UUID=87eefced-93ec-4418-9df7-ead508bb8240 /home           ext4    relatime        0       2
# swap was on /dev/hda3 during installation
UUID=940524b9-42eb-4ed2-813b-05ca5996c62a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by tiresia on 2010-01-07
Are you using a LiveCD? Have you tried to erase the whole HD (after making a BACKUP!)?

---

### Post by Praxicoide on 2010-02-07
Sorry for not responding, but I've pretty much given up on this Mac.

The problem I would have about deleting the entire harddrive is deleting the bootstrap partition. Is it OK to delete that?

EDIT: And the only solution would then be to wipe the hard drive clean?

---

