---
title: "Access Primary Ubuntu Drive from Windows Slave"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by gr8gatzb on 2008-04-03
I followed the installation here with Windows XP on the slave and Ubuntu 6.06 on the master:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

I am having hard drive recognition problems from each side. In Windows, I can't see the master Ubuntu drive. It seems as though a new drive was recognized that wasn't there before, but its a small Dell Utilities partition on the slave drive. Under the Hardware Profile of the System window in the Control Panel, it recognizes the correct hard drive, but it's not showing up in the Windows Explorer.

From the Ubuntu side, I can't access the Windows slave drive. It recognizes it in the Disk Manager, but I don't have permissions to access it. It is assigned to the root owner and group. I can change to user root in the shell and then access the drive via the shell, but I can't access it outside of the shell as a non-root user. When I try to change permissions, owner, and group as root user of the drive, I get an error along the lines of "this drive is read-only".

Any ideas how to get this to work from both sides?

Thanks!

---

### Post by Slushdoot on 2008-04-03
To use Windows to mount and use the ext3-formatted partition Ubuntu uses you need an ext* driver.  I've used [ext2fs](http://www.fs-driver.org/) for this purpose in the past and it's worked flawlessly.

---

### Post by dannyboy79 on 2008-04-03
> **gr8gatzb said:**
> I followed the installation here with Windows XP on the slave and Ubuntu 6.06 on the master:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

I am having hard drive recognition problems from each side. In Windows, I can't see the master Ubuntu drive. It seems as though a new drive was recognized that wasn't there before, but its a small Dell Utilities partition on the slave drive. Under the Hardware Profile of the System window in the Control Panel, it recognizes the correct hard drive, but it's not showing up in the Windows Explorer.

From the Ubuntu side, I can't access the Windows slave drive. It recognizes it in the Disk Manager, but I don't have permissions to access it. It is assigned to the root owner and group. I can change to user root in the shell and then access the drive via the shell, but I can't access it outside of the shell as a non-root user. When I try to change permissions, owner, and group as root user of the drive, I get an error along the lines of "this drive is read-only".

Any ideas how to get this to work from both sides?

Thanks!

windows can only see Ubuntu drives (formatted with ext3 filesystem) using the fs driver found here ([http://www.fs-driver.org/](http://www.fs-driver.org/))

and ubuntu should be able to mount and see your ntfs windows drive using the ntfs-3g driver. You would find out the hard drive and partition using sudo fdisk -l, then add an entry to your /etc/fstab file like this:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

