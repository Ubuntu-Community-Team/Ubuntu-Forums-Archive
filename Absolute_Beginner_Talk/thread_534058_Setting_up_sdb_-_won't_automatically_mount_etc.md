---
title: "Setting up sdb - won't automatically mount etc"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by halrogers on 2007-08-24
Many reboots and tries, here's where I'm at

VMware -- added 8 GB drive to existing (and working) Ubuntu

sudo cfdisk /dev/sdb -- add a partition of 8000, Type 83 (Linux) Non bootable
and it shows up as Name sdb1

add another partition of about 500 meg, type 82 (Linux swap / Solaris) to make it
look similar to the primary drive sda (with two partitions)

Write partition info

------

sudo mkfs -t ext3  /dev/sdb1  -- goes through looks fine, and cfdisk shows ext3

Create a mount point   /mnt/newdisk  - made this okay
sudo chmod go+x /mnt/newdisk  - no complaints

MOUNT
sudo mount -t ext3 /dev/sdb1 /mnt/newdisk
no complaints here

Use computer to find /mnt/newdisk in filesystem, can open it 
but CANNOT add directories or files. 

Continue to edit   sudo gedit /etc/fstab

Here is where I've tried everything I can think of and nothing mounts automatically
and nothing gives me permissions

examples in my fstab file
# /dev/sdb1 / ext3 rw,errors=remount-ro 0 0
#/dev/sdb /mnt/newdisk ext2 defaults 0 0
#  -- next appears, but not automaically
/dev/sdb1 /mnt/newdisk ext3 defaults 0 0
#next does not allow rw
#/dev/sdb1 /mnt/newdisk ext2 defaults 0 0
#/dev/sdb1 /media/disk ext3 defaults 0 0 

the one that is acive (not commented) is  /dev/sdb1 /mnt/newdisk ext3 defaults 0 0

but it doesn't mount automatically, and when I do click on the disk in "computer"
it ends up mounting on  media  and not mnt  and no read or write permissions

I could login as root (figured that out with help)  and edit the read write
permissions, but why not with chmod ??

Bottom line:

Would someone go through STEP BY STEP a procedure to add a hard disk
to ubuntu that

1. mounts automatically
2. has read/write permissions to users other than root
3. includes all the required steps (I think I have done them all)

or send me an e-mail with instructions for THIS problem, and not a
generic "how to add a drive" that is helpful, but can't be verified since
details are left out and only general ideas are there.

One other issue: If I tell it to mount sdb1 it seems to mount sdb2, the
smaller partition only. If I tell it to mount sdb (leaving off the 1 or 2)
it shows both partitions

When i click on the drive it asks for a password, then shows it on the
desktop as "drive" but still doesn't allow Read/Write

Sorry this is so long, but trying to be complete.

Thanks for any help -- I've spent hours reconfiguring things 
learning how to use the terminal mode, cfdisk, mkfs, sudo, gedit, etc.

Hal

---

### Post by livestockPimp on 2007-08-24
your problem is in /etc/fstab.
in the fourth column is mount options, by default this will mount the drive for root use.
you need to give it rw user permissions. read "man mount" to work out what options you need to set or read a guide on using fstab.

---

