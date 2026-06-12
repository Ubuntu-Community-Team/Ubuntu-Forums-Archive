---
title: "NTFS defrag"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by warrior24 on 2008-01-03
Hi guys is there any way to defrag my NTFS partitions ? I searched in the forums but nothing new.  Or should I just reformat to a new file system. In that case which file system to I use for storing music and pictures.

---

### Post by taurus on 2008-01-03
Why not use ext3.  It's much better than any ntfs filesystem combined.

---

### Post by asmiller-ke6seh on 2008-01-03
If you are using NTFS because you plan on having Window$ co-resident, just defrag from the Window$ side. Otherwise, you will be better off using ext3 - manual defrag is not necessary with this FS.

---

### Post by warrior24 on 2008-01-03
Yes I don't ever plan on using wincrapdows.  So once I reformat using partition editor I installed pysd to auto mount the volumes.

---

### Post by nrfool on 2008-01-04
what if this is a external hard drive that is going to be plugged into a windows box from time to time? 
Is there a tool to defrag the hard drive in linux?

---

### Post by warrior24 on 2008-01-04
why not then defrag it in windows.  I know there is some drive you can install in windows to make it read different file formants but don't remember what its called.

---

### Post by warrior24 on 2008-01-04
[http://sourceforge.net/project/showfiles.php?group_id=182608](http://sourceforge.net/project/showfiles.php?group_id=182608)


This should work I am gonna give it a try.

---

### Post by utkjamie on 2008-03-21
Has anyone found a way to defrag an NTFS partition from Linux? I need to resize an NTFS partition used by Windows with GParted. The problem is that Windows loves to leave fragments of files all over the hard drive and I need to leave the unused empty space on the partition at the end of the partition in order to resize it. Some of those file fragments are unmovable when Windows is running so running a defrag inside Windows isn't an option. We would think Microsoft would have found a solution to this problem since Win95 was released but this obviously isn't the case. Running a defrag from a LiveCD would work, but I haven't found one to do the job yet and I'm not going to drop a lot of money on an offline defragger I'll only use once (especially since this should be an option provided by Microsoft).

I'm dying for a solution here since I have somewhere between 4 and 9 GB of space being wasted on my WinXP partition that I'd love to free up for Linux use.

---

