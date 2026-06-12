---
title: "How did Ubuntu write to this ntfs?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-03-04
Hello
Before going to Ubuntu I purchased a program called "Accountz", whose files can be read or written to either in Windows,  Mac,  or Linux.  After a bit of tweaking, this has been up and running for about a week now and seems to be working well.
The accounting programs are seated in the "C" drive in program files (Windows Files), and I cross over to that file (via 'media') when working on them in Ubuntu, which is most of the time.

I have just realised that the Windows partition is ntfs,
and remembering  from my lessons that Ubuntu does not write to ntfs, I am surlrised that it is doing it all fine.

Can anyone suggest how this can happen? How come it writes all the data I request to the ntfs partition with no problem?

I have not installed the programs from the Synaptic Package Manager which enable Linux to write to ntfs files.

Looking forward to replies.

Regards

John

---

### Post by lswest on 2008-03-04
if you're running Ubuntu 7.10 then it comes with ntfs-3g pre-installed, which allows writing to NTFS partitions, no problem.  Otherwise Feisty could read ntfs partitions fine, and once you installed ntfs-3g it would write to them as well.

---

### Post by Andavane on 2008-03-04
ntfs-3g is installed indeed.
Thanks very much for the information!
Kind regards
John

---

### Post by lswest on 2008-03-04
no problem, happy i was able to help ^^

---

