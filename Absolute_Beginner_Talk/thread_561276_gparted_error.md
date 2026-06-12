---
title: "gparted error"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by ident4 on 2007-09-27
Hi

I was using[ this]("http://georgia.ubuntuforums.org/showthread.php?t=508927") tutorial to remove Ubuntu.

All went well until step 9b - resizing the windows partion. 
Just after gparted stated resizing to take up the empty space, it displayed some sort of error message saying it couldn't do it ('fraid I didn't keep a note of what it said)

When I closed the error message, the graphic  showed my C drive as being resized but empty. :eek:

But when I restarted, I was surprised that windows started normally and everything seems fine.

*Disk  Mangement* in windows reports that the partition is the right size and 'Healthy' and when I tried Gparted again everything seems fine there as well.

Is there any way I can double check that everything is as it should be?

---

### Post by mridkash on 2007-09-27
A common error that gparted throws is when it tries to resize a mounted partition. 
If you see a icon for C: on the desktop then it is mounted. unmount it. and then try gparted.
If still it throws some error then the filesystem may have errors, from windows do a "chkdsk -f" (in command prompt, without quotes)
if it finds some errors it'll correct them automatically.
Also, make sure that the partition is defragmented. On windows in run window type defrag.msc and defragment the c drive

Then try gparted again. If still errors, post them here!

---

