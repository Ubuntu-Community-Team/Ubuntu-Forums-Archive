---
title: "Problem with GUI at startup"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Sitting Duck on 2007-12-14
Greetings,

I lost my graphical interface this morning.

When I try to boot my computer, everything seems to work normally until I reach the final step just before login.  I get the following messages:

Starting up ...
Loading, please wait...
kinit: name_to_dev_t (/dev/disk/by-uuid/***********************) = hda5(3,5)
kinit: trying to resume from /dev/disk/by-uuid/************************
kinit: No resume image, doing normal boot ...

Ubuntu 7.10 Desktop tty1

------end of message----- (where ************ stands for a long line of apparently random characters)

I have no idea what's going on and would appreciate any help.

Thank you in advance!

---

### Post by simon_is_learning on 2007-12-14
Well, the numbers  you masked is the UUID(name) for the partition, all the information about the disk is in the file /etc/fstab

The problem you have encounterd seems to have happend to some others to:

[http://ubuntuforums.org/showthread.php?t=385869&page=1](http://ubuntuforums.org/showthread.php?t=385869&page=1)

[http://ubuntuforums.org/showthread.php?t=479545&page=2](http://ubuntuforums.org/showthread.php?t=479545&page=2)

[http://ubuntuforums.org/showthread.php?t=484296](http://ubuntuforums.org/showthread.php?t=484296)

But what you can do is reboot, and when you see the progress bar press alt-F3, then you will se what happens when you start up the system. If you can see any other error messages you can post them here. But hopefully you'll find something in the threads above.

---

### Post by Sitting Duck on 2007-12-14
Thank you Simon!

The problem is not fixed but I saw a few things worth trying in the threads you suggested. Meanwhile,  I booted the problem computer using a Lve CD and mounted the hard disk so I can copy on DVDs all the important files I want to save from that hard disk.

Then I'll play alchemist and try to fix this (looks like a problem with xserver,xorg).  If I can't, I think I'll simply reinstall tomorrow.

Thanks again for the help.

---

