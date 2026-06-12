---
title: "Completely reformat fdisk/mbr harddrive"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by josephpford on 2007-12-10
Hello...

I am hoping someone can help me with this problem.  A long time ago (6 months) I was helping a friend with some computer problems on his windows machine and somehow my external 260gb usb harddrive stopped working.  Now, it *could* be a hardware issue, but I don't think it is.  Here's why:  After having problems on the windows machine, I plugged it into my ubuntu machine and ubuntu told me I had to enter a command into the terminal window before it would work in linux.  I dutifully performed the task Ubuntu told me to.  I'm sure you'd like to know what the command I typed is as much as I do, but I have no idea what it was.  

I think it did something to either my partition table or my bootsector or something else that is above my head.  

Is there a way to completely destroy everything on the harddrive so I can get this thing going again?  I've tried:

In windows: delete all partitions and create all new ones (no luck)
In Ubuntu: using gparted deleted all partitions and tried creating new partitions (no luck)
In Ubuntu: installing Ubuntu to the external USB harddrive (no luck)  I tried this option because I thought it would wipe out the "boot sector" area of the harddrive.

Any ideas?

Thanks,
Joe

---

### Post by josephpford on 2007-12-10
This is the error I get trying to install Ubuntu:

The ext3 file system creation in partition #1 of SCSI5 (0,0,0) (sdc) failed.

---

### Post by bumanie on 2007-12-10
To completely wipe a drive dban is meant to be as good as you can get. It can be run from a floppy, made into a live cd or run from a usb pen drive.
Worth a try.

---

