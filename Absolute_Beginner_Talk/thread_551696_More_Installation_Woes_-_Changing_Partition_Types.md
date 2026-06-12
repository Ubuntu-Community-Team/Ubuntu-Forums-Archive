---
title: "More Installation Woes - Changing Partition Types"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by CAD-MAN on 2007-09-15
Hi,

Just setting up my partitions on the Ubuntu Alternate Installation CD. Im aiming to dual boot Ubuntu alongside Vista. Here is what my partition structure looks like at the moment:

#1 primary   123.3MB    K fat 16    /media/sda1
#2 primary       6.5GB    K ntfs        /media/sda2
     unusable      4.2GB          unusable
#3 primary      47.2GB   K ntfs        /media/sda3
#6 logical        85.3GB   f  ext3       /
#7 logical          2.0GB   f  ext3
#8 logical        12.0GB   f  ext3
#5 logical          2.7GB   K fat32      /media/sda5



Ok, #1, #2, #3, #5 were all there before I started messing around with this (brand new - arrived this morning) laptop. #6, #7, #8 were created by me out of the free space acquired after shrinking Vista's partition (#3). #6 will hopefully be where Ubuntu resides, #7 will hopefully be swap space, and #8 will hopefully be a partition shared between Ubuntu and Windows (for music, photos, the occasional file that I may need to copy from one OS to another, etc).


Now that you have the idea of the setup im going for, I have a couple of questions:

[LIST]
[*]Im guessing that the Ubuntu partition (#6) needs to be listed as 'primary' instead of 'logical'? I can't find a way to change this in the Alternate CD
[*]Where do I mount #7 and #8 (Swap space, and the shared partition)?
[/LIST]


Thanks in advance

---

### Post by benerivo on 2007-09-15
> Im guessing that the Ubuntu partition (#6) needs to be listed as 'primary' instead of 'logical'? I can't find a way to change this in the Alternate CD
Where do I mount #7 and #8 (Swap space, and the shared partition)?


I don't think #6 needs to be primary. I always though logical just referred to partitions that were inside an extended partition (which i'm guessing is #4 - and contains #5, #6, #7, and Eight).

The swap partition would mounted by itself as swap by the installer. You do not have to generate a swap mount point manually to be part of the linux filesystem. The shared partition would be mounted inside/media, but again this would be an automatic process handled by the installer. During installation you would be better off formatting #8 as ntfs if it is to be used as a shared partition with Vista.

---

### Post by mikewhatever on 2007-09-15
The Ubuntu partition does not have to be primary, also, there is a limit of 4 primary partitions per hard drive. That means that if you already have 4 primary ones, you'd need to delete one to create new partitions.
The swap partition is mounted as swap, and the shared one as, /media/shared.

---

