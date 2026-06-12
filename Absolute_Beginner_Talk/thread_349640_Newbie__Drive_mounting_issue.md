---
title: "Newbie:  Drive mounting issue"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by maceylou on 2007-01-30
I have a 160G hard drive. I partitioned it C:/ & D:/ . I run windows XP and all my music, pics ect... are on D:/ I installed ubuntu 6.06 yesterday on the same hard drive. Ubuntu has its own partition on the same hard drive. I want to transfer the data from D:/ to ubuntu6.06. I am having no such luck. I can see the C:/ & D:/ on ubuntu however it will not let me view or open any files. It says I do not have access. Please help me.
Yes I am a newbie.
Chris

---

### Post by taurus on 2007-01-30
How did you mount your partitions?  Did you mount them from a terminal or did you go through /etc/fstab?

What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Brunellus on 2007-01-30
> **maceylou said:**
> I have a 160G hard drive. I partitioned it C:/ & D:/ . I run windows XP and all my music, pics ect... are on D:/ I installed ubuntu 6.06 yesterday on the same hard drive. Ubuntu has its own partition on the same hard drive. I want to transfer the data from D:/ to ubuntu6.06. I am having no such luck. I can see the C:/ & D:/ on ubuntu however it will not let me view or open any files. It says I do not have access. Please help me.
Yes I am a newbie.
Chris
Post detached and moved to its own thread.  If you have a technical question, it is always preferrable to ask it in its own thread rather than hijacking a thread that is already in progress, and taking that thread off-topic.

First:  there is no C:\ D:\ or any of that business in Ubuntu.  We handle disks differently.  We speak of physical disks as **devices** and we speak of the data on those disks as parts of the **filesystem**

In order to have access to the data on a **device** we must **mount** that device to some point in the filesystem.  

To do this, you should follow the directions on [this page in the wiki](https://help.ubuntu.com/community/MountingWindowsPartitions).

Note that if your Windows partition is formatted in Windows XP's native ntfs filesystem, it you can only READ (**NOT WRITE**) to that partition.  Write-access to ntfs filesystems is experimental, not officially supported, and may result in irrecoverable data corruption.  You have been warned.

Also:  if you installed Ubuntu onto what used to be C:\ in Windows...you have just lost everything on C:\.  Remember that you installed a whole OS, which means reformatting that partition.  The other (D:\) partition should still be untouched.

For more complete guidance on living with systems with Windows, consult [this wikipage](https://help.ubuntu.com/community/WindowsDualBoot)

---

