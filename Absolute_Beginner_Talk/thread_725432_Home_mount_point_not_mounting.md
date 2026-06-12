---
title: "/Home mount point not mounting"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2008-03-15
I just finished my install of ubuntu on my new system. This system uses software RAID1 as described [here.]("http://advosys.ca/viewpoints/2007/0/setting-up-software-raid-in-ubuntu-server/")

During installation, I created the following partitions...
8 GIG Swap
120 GIG Root
120 GIG Home
500 GIG undeclared ext3 (future use for data)

The system just booted for the first time. Problem is, the Home folder is on the Root Partition, and not on its own partition. The 500 undeclared didn't mount at all. I can manually mount these partitions, but I need the home to mount automatically, and place users /Home folders there. How can I make the system mount these automatically and mount home where it belongs?

My fstab...
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md1
UUID=8409778b-c4e4-4c79-9ff1-7c01416b89f0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/md2
UUID=a53a4b6a-43e6-48f8-8e22-8fa2a1ca2b33 /home           ext3    defaults        0       2
# /dev/md0
UUID=d8d1aee7-8b8d-4ce6-81d0-70b436cd9fa7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       
```

Thanks

---

### Post by bren on 2008-03-15
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by munkyeetr on 2008-03-15
Type the following into a Terminal window and post the output:
```

blkid

```

---

### Post by The Cog on 2008-03-15
Your fstab looks reasonable. Two ways to check it:

See if **sudo mount -a** makes the home partition mount. If it does then I have no idea why it doesn't mount at boot. If it doesn't then there's somethong wrong with fstab.

use the command **blkid** and check the UUID matches the one in fstab.

---

### Post by ant2ne on 2008-03-15
```
ant2ne@2ne-buntu:~$ blkid
/dev/sda1: UUID="e30b9862-001e-cd7b-f0df-80085dec7554" TYPE="mdraid" 
/dev/sda2: UUID="ade95d20-b811-1ce2-ae8d-e215946127b3" TYPE="mdraid" 
/dev/sda5: UUID="f3d4a4bb-01cc-0641-f55b-d41b9aea5c69" TYPE="mdraid" 
/dev/sda6: UUID="4913c878-e596-437e-5ab0-d738f6ee7f55" TYPE="mdraid" 
/dev/sdb1: UUID="e30b9862-001e-cd7b-f0df-80085dec7554" TYPE="mdraid" 
/dev/sdb2: UUID="ade95d20-b811-1ce2-ae8d-e215946127b3" TYPE="mdraid" 
/dev/sdb5: UUID="f3d4a4bb-01cc-0641-f55b-d41b9aea5c69" TYPE="mdraid" 
/dev/sdb6: UUID="4913c878-e596-437e-5ab0-d738f6ee7f55" TYPE="mdraid" 
/dev/md0: UUID="d8d1aee7-8b8d-4ce6-81d0-70b436cd9fa7" TYPE="swap" 
/dev/md1: LABEL="root" UUID="8409778b-c4e4-4c79-9ff1-7c01416b89f0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/md2: LABEL="homes" UUID="a53a4b6a-43e6-48f8-8e22-8fa2a1ca2b33" SEC_TYPE="ext2" TYPE="ext3" 
/dev/md3: LABEL="data" UUID="8ac81a21-7870-474c-9710-d49f403195f1" SEC_TYPE="ext2" TYPE="ext3" 
```

---

### Post by ant2ne on 2008-03-15
> **bren said:**
> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)I tried that so my fstab looks like...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md1
UUID=8409778b-c4e4-4c79-9ff1-7c01416b89f0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/md2
/dev/md2 /home ext3 nodev,nosuid 0 2
#UUID=a53a4b6a-43e6-48f8-8e22-8fa2a1ca2b33 /home           ext3    defaults        0       2
# /dev/md0
UUID=d8d1aee7-8b8d-4ce6-81d0-70b436cd9fa7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/md3 /media/md3 ext3 nodev,nosuid 0 2
ant2ne@2ne-buntu:~$ 

```
Still no luck. 

This is really annoying me.

---

### Post by ant2ne on 2008-03-15
This seems to be working....

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md1
UUID=8409778b-c4e4-4c79-9ff1-7c01416b89f0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/md2
/dev/md2 /home ext3 nodev,nosuid 0 2
#UUID=a53a4b6a-43e6-48f8-8e22-8fa2a1ca2b33 /home           ext3    defaults        0       2
# /dev/md0
UUID=d8d1aee7-8b8d-4ce6-81d0-70b436cd9fa7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/md3 /media/md3 ext3 nodev,nosuid 0 2
/dev/md2 /media/md2 ext3 nodev,nosuid 0 2
```

Except; 
I would like the home to show up in the Places->Computer list.

Also, when I'm in a random location of the files system... is there a way to tell what physical HD I'm in? Linux mounts stuff and it blends in with other directories.

---

