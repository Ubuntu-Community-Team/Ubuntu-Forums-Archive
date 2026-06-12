---
title: "[Before I install...] single-user mode"
date: 2011-04-17
forum: Apple Hardware Users
---

### Post by cfr42 on 2011-04-17
[LEFT]I want to set up my G4 PowerBook to dual boot linux and os x. Right now, the disk is partitioned with one partition for OS X and the other is empty. I'm not sure I've done this quite right so I may need to redo things but am not certain yet.
[/LEFT]
 
Before I actually install anything, I would like to be sure that I know how to boot into single-user mode if I need to. That is, will an install of linux change the method for doing this? Will I still get the familiar prompt just booting with command and s or will I need to do something different?

If it works in the same way, do you end up in single-user mode for the OS X file system? If, say, you run fsck, is that being run on the OS X system at that point?

I have never had two bootable volumes on an internal disk before and I'm a bit confused about exactly how things will work.

Since I am perfectly capable of rendering my system unbootable and since I do not typically carry my OS X install disks around with me, I want to be sure that I can get to single-user mode and make changes to the OS X file system if I need to. (Since this is likely to be my working system for at least a while, this is the one I need to be sure I can fix.)

And before anybody says so, I have absolutely no intention of installing anything without testing a current clone to ensure it is bootable and otherwise appears to be working.

---

### Post by cfr42 on 2011-04-18
Sorry but I'm not clear whether that's an answer, a further question or a query because my original question wasn't clear.

If you have a full version of OS X (i.e. on a desktop or laptop rather than an ipad or iphone) and you hold down command/apple + s as the computer boots, you reach single-user mode which is a command line interface with root privileges. At this point, the OS X boot volume is not mounted so it is possible to repair damage to the file system by using e.g. /sbin/fsck -fy. (The -f is necessary else fsck refuses to make changes to a journaled volume. If the volume is not journaled, you can just use -y instead.)

At least, that's what happens if there is a single bootable volume on the internal disk with OS X.

What I'm not sure about is whether you get to single-user mode using the same method if you have Ubuntu on one partition, say, and OS X on another. In this case there would be two bootable volumes on the internal drive. Do you have to do something different to get into single-user mode to repair the OS X volume?

Booting into single-user mode is especially useful, I find, because it does not require me to have the OS X install CD with me or another bootable OS X volume. (The first is Apple's preferred method of repair but one that I rarely use - I usually find it is easier to use fsck etc. in single-user mode to fix issues.)

So my question is just: what difference to the boot-with-command/apple-plus-s -> immediately get single-user mode to repair OS X volume will having Ubuntu on another partition make?

---

