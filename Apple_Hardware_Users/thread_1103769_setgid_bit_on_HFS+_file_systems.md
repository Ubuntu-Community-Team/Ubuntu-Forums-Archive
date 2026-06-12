---
title: "setgid bit on HFS+ file systems"
date: 2009-03-23
forum: Apple Hardware Users
---

### Post by coiske on 2009-03-23
I'm setting up a multiuser dual-boot (Intrepid/Leopard) system.  I created a nonjournalled HFS+ data partition, and I'm trying to set it up with access permissions that are respected in both OS's.

Specifically, I want each user to have his/her own private directory on the partition that is not readable by others.  Further, I want a shared directory on the partition that everyone can read and write to.  Files created in the shared directory need to be editable by anyone, not just their creator.  And these rules need to be respected by both Intrepid and Leopard.

I was able to get the private directories working in both OS's.  But the shared directory is proving very difficult to implement.  I set the umask to 007, so new files would be rw-rw---- or rwxrwx---.  And I assigned the shared directory to a group that all users belong to.  Finally, I used the setgid bit (drwxrws---), so files created in the shared directory would belong to the shared group.  This worked fine in Leopard, but not in Intrepid.

Problem is, the Intrepid kernel doesn't seem to respect the setgid bit on mounted HFS+ filesystems.  It shows that the bit is set, but doesn't behave accordingly.  New files that Intrepid creates in the shared directory end up belonging to the user's private group, not the common group that owns the directory.    I even tried passing the suid option to mount, to no effect.

1) Is there any way to get the Intrepid kernel to respect the setgid bit on HFS+ filesystems?
2) If not, is there any other way to implement the sort of directory permissions scheme I described on a HFS+ filesystem?
3) if not, is there any filesystem other than HFS+ that works well under both Leopard and Intrepid, and could handle the directory permissions scheme I'm going for (in a way that's respected by both OS's)?

Thanks for your time!

---

### Post by jiho on 2009-05-27
I have the same problem for almost the same reasons. OS X respects the setgid bit but Ubuntu does not. I have:
Jaunty up to date with proposed and backports
Linux kernel image for version 2.6.28 on x86/x86_64
hfsplus 1.0.4-12build1
hfsutils 3.2.6-11build1

I would very much welcome any piece of advice. Thanks in advance.

---

### Post by dan000 on 2010-06-08
I'd like to renew this question, because I have the same problem. The setgid bit on directories on HFS+ partitions seem to be ignored on Linux (at least on Ubuntu).

I'd like to file a bug, but I'm not sure which package the bug belongs to.

---

### Post by Frobber on 2010-06-09
Have you looked at Dscl on the Mac side? How about the advanced settings for your Mac Users?

Between the two, I think you can achieve what you are attempting.

---

