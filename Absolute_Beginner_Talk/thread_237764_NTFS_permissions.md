---
title: "NTFS permissions"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by paxcow on 2006-08-16
When i try to accsess my NTFS backup drive i get this error message.
You do not have the permissions necessary to view the contents of "disks-conf-hdb1"

I went to [http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_).
28NTFS.29_manually.2C_and_allow_all_users_to_read_only
but that did nothing.

So here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by ComplexNumber on 2006-08-16
there is no ntfs mount point in your fstab. first, **MAKE A BACKUP** of your fstab file. always make a backup of ANY important files that you edit. and keep them in safe place that you can easily get to just in case you need to restore the original.  then do the following:
a) install the relavant ntfs modules such as ntfs-kmod, ntfs-kmod-common, ntfsprogs. NOTE: i'm not entirely certain which of these are absolutely necessary.
b) fire up the terminal and go to /media.
c) type in 'sudo mkdir ntfs', so that you now have a /media/ntfs directory.
d) add the following AT THE END of your fstab:

/dev/hdb1               /media/ntfs          ntfs    ro,users,umask=0222      0 0


this will give you read only access to your ntfs partition. when you next log in, you will be able to access your ntfs drive by going to /media/ntfs. if you wanted to have access immediately after doing the above changes, just type in 'sudo mount -a /media/ntfs' in the command line. the entry in fstab indicates which filesystems are mounted at boot time. if you wanted your ntfs partition to be automatically mounted at boot time, then place an entry in fstab. if you're not bothered about that, then no entry is required in fstab (just mount in manually each time).

---

### Post by TMR on 2006-08-16
Hi,

Try typing '**mount**'.  I get 

/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
[... blah blah deleted]
/dev/sda3 on /tmp/disks-conf-sda3 type ntfs (rw)

I also get the same message you get.  So I do this:

**sudo umount /dev/sda3**

That unmounts it.  Make a mountpoint, eg:

sudo mkdir /media/ntfs

Then mount it:

**sudo mount -r -t ntfs -o umask=0222 /dev/sda3 /media/ntfs**

Then you can read it.  The -r means read-only (don't try writing to NTFS from other O/S, IMHO); the -t is the type, the -o introduces the options (in this case the permissions mask); then the device, then the mount point.

If you always want to be able to see it you should edit your fstab:

[B]sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab[/B]

Then append to the bottom of the file:

**/dev/sda3 /media/windows ntfs umask=0222 0 0**

Remember to use your partition where I have used /dev/sda3 and your mountpoint where I have used /media/windows

TMR

---

### Post by paxcow on 2006-08-16
It works now, thanks.

---

