---
title: "Attempting Install:  Problem with Windows Partition"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by benditlikebecker13 on 2007-05-11
I am finally attempting to install Feisty, but I am running into a problem with my NTFS partition.  I am trying to follow the instructions found here:

[WindowsDualBootHowTo]("https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo")

I attempted the first instructions by trying to partition my drive with the Unbuntu installer.  I got a general error that said it could not partition drive as I selected (I have an 80 gig, I was trying to make NTFS partiton 20gig so I could have 50+ leftover for Unbuntu).  So then I tried the second part of the instructions.  Download the System Restore/Tools disc and tried to boot from it.  The problem I have with that is I get an error when botting into that.  I get:

"Unable to find Linux Kernal"

So what do I do... Part of my wants to say screw it and go for Unbuntu only, but I would like to keep Windows so my (very) computer illiterate wife can still use the PC once and a while.  Thanks.

---

### Post by dstew on 2007-05-11
Do you have XP or Vista on that ntfs partition?
If it is XP, you can shrink the partition safely with the GParted tool on the Ubuntu Live CD. If it is Vista, you need to use the Vista volume management tool (in Vista itself).
The usual reason that you cannot shrink a partition is that it has not been defragmented, so there are some used blocks in the area to be shrunk. The next reason is that is has some bad blocks. You can run chkdsk -f from Windows to fix that problem. Another problem is the "green bar" that is immovable inside the partition. This is usually a Windows swap file. You have to go into Windows and turn of the swap file, then defragment.

EDIT: I would definately go for dual-boot in your situation.

---

### Post by benditlikebecker13 on 2007-05-11
> **dstew said:**
> Do you have XP or Vista on that ntfs partition?
If it is XP, you can shrink the partition safely with the GParted tool on the Ubuntu Live CD. If it is Vista, you need to use the Vista volume management tool (in Vista itself).
The usual reason that you cannot shrink a partition is that it has not been defragmented, so there are some used blocks in the area to be shrunk. The next reason is that is has some bad blocks. You can run chkdsk -f from Windows to fix that problem. Another problem is the "green bar" that is immovable inside the partition. This is usually a Windows swap file. You have to go into Windows and turn of the swap file, then defragment.

EDIT: I would definately go for dual-boot in your situation.

I have XP.  Is the GParted tool the tool that is used when attempting an install Unbuntu?  Because that is what I had problems with.  I think the disk defrag may be the problem.  I have all the "blocks" moved to the front of the drive with the exception of the Green swap file and some blue lines to the right of that.  I will try and figure out how to turn off the Swap File in Windows and then go back and try to install with the Live CD again.  Also, I did do a check disk prior to install.

---

### Post by benditlikebecker13 on 2007-05-11
I think I got it now.  I was trying to use the partition tool that came up during install.. Now that I found GParted it seems to be working.  Keeping my fingers crossed.

---

### Post by godssiren on 2007-05-15
I am having the same problem with the green area in the defrag window... but I don't know how to turn off the swap in windows... and I have 2 green unmoveable file areas... I just uninstalled a bunch of programs I haven't used in the last 2 yrs, and freed about 10 GB of hard drive space... now I'm running defrag again, but I don't know what to do with those green areas. If you figured out how to fix this problem in XP, please let me know ^_^

---

### Post by dstew on 2007-05-16
The green areas are Windows swap files. Shut off the swap file option in Windows, defragment again, and the green areas should be gone.

---

### Post by godssiren on 2007-05-16
Just to clarify, the only thing I could find that seems right is :
Go to My Computer(right click) > Properties > System Properties > Advanced Tab> Performance( Settings) > Advanced Tab > Virtual Memory (change) ... and then select "no paging file"?
Then defragment... right?
I will try it. (I can't imaging that it will kill my computer since MS actually lets me touch it... and without a warning pop-up )

---

### Post by dstew on 2007-05-16
Yes, I think that is it.

---

### Post by godssiren on 2007-05-17
Ok,
So regarding my last post, I was right about it's location in XP, and I turned it off and YAY, the green was gone! ... unfortunately, I hit defragment one more time hoping to clean up a few fragmented straglers that had been created when I turned off the swap.  This took care of the fragmented files, but suddenly stuck some new ones (blue) out on the end of the drive even farther than the "unmoveable" ones had been. I have tried defragmenting a few more times and very very little happens... what's more... nothing happens to those blue files now stuck at the end of the drive, and they won't budge.
 I have no idea which files they are, so I can't move them manually, or decide if I just don't care about them enough to write over them when I resize.

Any advice/ help?

---

