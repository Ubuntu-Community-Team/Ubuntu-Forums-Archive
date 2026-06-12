---
title: "Recovering deleted files (XPUbuntu) Help!"
date: 2013-02-15
forum: Any Other OS
---

### Post by jayaq32 on 2013-02-15
Hi everyone,

I was prepping my old xp system for Ubuntu 12.04 and ran into an issue that's probably more of an xp question (unless Ubuntu can help?). I love this community and I really don't know what better place I'd rather turn to for this. :

I have 2 partitions on my xp system:

Partition #1 = C:
Partition #2 = D:

C: = OS
D: = Data

Both NTFS.

I assumed Ubuntu would require the entire disk + partitions (for re-configure) during the installation so I began backing up and clearing out my D: partition where all my data was.

In the middle of backing up D: I accidentally deleted 2 important directories:

Photo Folder #1
Photo Folder #2

During the delete, a prompt came up saying, "This directory is too big for the Recycle Bin, permanently delete it?" (Paraphrasing).

I mistakenly hit yes.

I believe the prompt was referring to Photo Folder #2.

When I realize my mistake, I naturally go into the recycle bin and find that only Photo Folder #1 is available for restore and not Photo Folder #2.

I undo delete to see what luck I may have and only Photo Folder #1 comes back. 

Yay!

But what about Photo Folder #2? 

Too big for Recycle Bin? 

At this point it's suggested I use data recovery software (like Recuva) to recover that directory and files.

This is the only thing preventing me from installing Ubuntu. I don't want to overwrite the disk unless I could recover that directory.

Questions:

1. I was told not to 'save' or  'write' anything to the disk/partition where the deleted files were located as this will save over the blank indexed space on the disk where Photo Folder #2 was located. Did "Undo Delete" (which restored Photo Folder #1)  rewrite to the disk or this space? Or was it restored to its original space on the hard disk?

2. Does any know if doing a system restore to an earlier date will restore files on a separate partition?

I would sooo much like to recover Photo Folder #2 before moving forward with the Ubuntu install. I know it's still on the hard disk somewhere. I know this is more of an XP question but I just don't know where else to turn to. This is the only thing preventing me from completing my migration to Ubuntu.  

Any help is appreciated! 

Thank you!

---

### Post by howefield on 2013-02-16
Thread moved to "*Other OS/Distro Talk*" forum.

First off, Ubuntu won't need you entire disk for itself. It is very neighbourly to other operating systems. ;-) 

Folder 1 will have been restored to it's original location, so use Recuva to try and find the contents of Folder 2. It is very good but there a number of pretty decent freeware applications for windows that will do this.

I am not 100% sure, but I doubt System Restore extends to your data drive. So you will need Recuva or something similar.

---

### Post by jayaq32 on 2013-02-17
> **howefield said:**
> Thread moved to "*Other OS/Distro Talk*" forum.

First off, Ubuntu won't need you entire disk for itself. It is very neighbourly to other operating systems. ;-) 

Folder 1 will have been restored to it's original location, so use Recuva to try and find the contents of Folder 2. It is very good but there a number of pretty decent freeware applications for windows that will do this.

I am not 100% sure, but I doubt System Restore extends to your data drive. So you will need Recuva or something similar.

I was able to recover my files successfully using Pandora Recovery and succesfully install Ubuntu!! . I didn't even need to do a deep scan to recover Folder 2!!!

Thank you so much for taking the time to reply too. 

And yes, you were right about Folder 1 being restored to it' original location on the actual HDD. The space that Photo 2 folder left behind was never overwritten or occupied even when Folder 1 was recovered using the 'Undo Delete' feature on Windows. This allowed the recovery software to easily detect and restore Photo 2 folder.

Anyone coming across this thread that may be having the same circumstance: *do not save anything or make any changes on your hard disk or partition where you accidentally deleted your file(s). *

Doing so may make recovery of your files more difficult if not impossible. If you accidentally delete something...STOP! Grab a copy of a trusted recovery software (like Pandora Recovery or Recuva - they are free to use). 

Of course, you may have to install the recovery software on the same disk that you want to recover from but the software is pretty lightweight and may not do any damage. You also have the option to install on another partition or even a USB stick to run the recovery.

When the software finds your deleted file(s) restore them to a different location such as another partition or external USB drive.

I was a bit skeptical that any recover software would work but to my surprise, I got my files back and I am a sailing pretty.

Good luck to anyone that finds themselves in this situation. Remember, you weren't the first to make this mistake. You don't be the last. And most importantly, you're not alone!

There is hope :)

---

