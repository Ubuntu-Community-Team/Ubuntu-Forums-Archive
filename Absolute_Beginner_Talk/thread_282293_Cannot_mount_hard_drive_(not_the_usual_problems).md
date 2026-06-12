---
title: "Cannot mount hard drive (not the usual problems)"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by greymaiden on 2006-10-22
Okay, I checked out the previous posts on this topic, as well as the guide to mounting a windows drive.  I've also consulted my Linux bible to no avail.  I've screwed some stuff up, I think.

First, I mounted hdb1 in the /abc directory and now I can't UNMOUNT it.  When I try the shell tells me that "unmount" isn't a recognized command (though it's in man).  

I need someone to walk me through this and troubleshoot as I go.  I followed all the directions given me on various forum posts and how-tos and I am totally lost.  

Here's my fidsk

> Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9348    75087778+  83  Linux
/dev/hda2            9349        9726     3036285    5  Extended
/dev/hda5            9349        9726     3036253+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9726    78124063+  83  Linux


Here's the thing: hdb1 is ALSO mounted in /abc (because I'm an idiot).  So thta's probably a problem.

So the drive appears to be mounted (ext3), but I can't acess it.  Can't save anything, nothing.  

I would really really appreciate some help here.  I'll send you tasty treats or something nice!

Thanks,
Jamie Lynn

---

### Post by David_T on 2006-10-22
Hello,
    You are probably looking for the umount command.  There is no "n" in umount.
    I don't know why you were able to pull up a man page for uNmount, although if you type "apropos unmount" it will lead you to the command umount.

---

