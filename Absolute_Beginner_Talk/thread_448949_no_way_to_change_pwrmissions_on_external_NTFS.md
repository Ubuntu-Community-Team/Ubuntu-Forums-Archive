---
title: "no way to change pwrmissions on external NTFS?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by mgh on 2007-05-19
I posted a thread, but for some reason did not get any email notification, and lost it.

I searched this forum for mounting permissions, and I am still not clear if this is possible.  I want to change automount permissions for any USB device I connect.  I am a complete newbie, so the command line is still tough for me to figure out.

My external drive is NTFS, and of course I do not want to lose all the data.

I'm beginning to wonder if I need to try and find room somewhere to backup all this data and reformat the drive in some Linux friendly format.  Before I can do that I better make sure XP will be able to read this drive also in whatever format I settle on.

Any ideas on what I can do?

Thanks for all help.

---

### Post by johannes on 2007-05-19
If you want write support for NTFS file systems check out the wiki:
[http://help.ubuntu.com/community/MountingWindowsPartitions](http://help.ubuntu.com/community/MountingWindowsPartitions)
However, NTFS support in Linux is apparently not very good and might not be completely stable. Using ext2 or ext3 is often recommended. They both have Windows drivers:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by mgh on 2007-05-20
With much help from another forum, I got a command code to change the umask for my external HHD.  So I can unmount the drive, then remount it with this command line, changing the umask to 022, which works great.

The problem is, I have to go through this every time I unplug this external drive.

What I am hoping for is a way to configure automount options, so that this is taken care of when any USB device is plugged in.

Any ideas?

Thank You

---

