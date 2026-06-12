---
title: "Partition Help!  using gparted"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by mkzimms on 2007-10-19
I would like to remove some of my storage used by vista and allocate it for ubuntu...
right now my gparted looks like this:

|--hda1,14 GiB, ext3--| |--------hda2, 56 GiB, ntfs--------| |-swap-|

if i shrink my ntfs partition i will end up with unallocated space after the ntfs partition.

|---ext3--| |---ntfs--| |-----**unallocated**------| |-swap-|

will i then be able to grow my linux (ext3) partition into that unallocated space with the ntfs partition in the way?  :confused:

note: im using the vista boot loader right now, not grub, so ntfs is flagged as boot.

Thanks in advance!

---

### Post by andrewsomething on 2007-10-19
Gparted can actually shrink and move partitions at the same time, so that the free space will end up on the left. That way you can grow the ext3 partition into it. 

|---ext3--| |-----unallocated------| |---ntfs--| |-swap-|

I would do this through a LiveCD personally. You can find a Gparted Live CD here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Or you could use Gparted from your Ubuntu LiveCD.

---

### Post by mkzimms on 2007-10-19
i saw move in the menu but didn't see how to actually make the partitions move... do i have to shrink the ntfs partition from the left to have the unallocated space come up before it, or will gparted move the unallocated space to the left of the ntfs partition on its own?

---

### Post by andrewsomething on 2007-10-19
You have to shrink it from the left. 

You might want to check out this tutorial:

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

