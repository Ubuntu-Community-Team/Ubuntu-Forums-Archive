---
title: "Multiple Partitoning Problems"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by mr.derp on 2007-04-03
I have been trying to install Xubuntu as a dual boot with Windows XP, and I have been having problems partitioning my hard drive. Basically it will not allow me to resize it using the partitioner in the installation, when I try to do it I get an error message saying something like "fix errors(if possible) on hda and try again". 

I have run chkdsk in windows fixing some boot errors, but that didn't help. I have also run the disk defragmenter multiple times. 

I even downloaded the system restore live cd and ran the partitioner on there, but when I do that it doesn't even let me resize the drive at all. Its just locked at the size for some reason. Also there is a little yellow caution type symbol next to the drive name. Whatever it means, I don't really know.

Anyways I have a NFTS system, the hard drive is a hda1, and its not mounted if any of that makes any difference.

Any suggestions on how to fix this problem would help so much.

---

### Post by freebird54 on 2007-04-03
> **mr.derp said:**
> I have been trying to install Xubuntu as a dual boot with Windows XP, and I have been having problems partitioning my hard drive. Basically it will not allow me to resize it using the partitioner in the installation, when I try to do it I get an error message saying something like "fix errors(if possible) on hda and try again". 

I have run chkdsk in windows fixing some boot errors, but that didn't help. I have also run the disk defragmenter multiple times. 


There is an option to force fixes from Windows - I use CHKDSK /F when i want something cleaned up.  Good idea to run defrag multiple times, but did you turn off the pagefile?  If it is a notebook, how about the hibernate file?  THEN Defrag twice...

If those 2 things don't do it, then ensure that Scandisk is told to check EVERYTHING, and fix what it can....

Hope this helps :)

---

