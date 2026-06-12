---
title: "Windows fails after re-partition"
date: 2013-11-27
forum: Any Other OS
---

### Post by shelvacu on 2013-11-27
So I have way too many partitions on a GPT table. My system is Ubuntu/Arch/Win 8 tri-boot. Recently, I needed more space on ubuntu, so I shrank the arch partition, and enlarged the ubuntu partition. I *thought* that I made sure NOT to touch the windows partition. However, after the repartition, Windows will not successfully get to the login screen. I will get a loading screen, then it goes blank and the backlight flashes until I cut power. Also, when I use gparted it says "Unable to read contents of this file system!", but I have successfully mounted, read, and wrote to said partition. I have no idea if this is related.

I tried running ntfsfix on the windows partition, it gave

```
Mounting volume... The disk contains an unclean file system (0, 0).Metadata kept in Windows cache, refused to mount.
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda5 was processed successfully.

```
From what I searched, the first line is a result of windows half-hibernating. I can't fix this, because I can't boot windows.

Arch and Ubuntu still work normally. Any ideas to get Windows to boot?

---

