---
title: "Another partition question"
date: 2007-10-12
forum: Apple Intel Users
---

### Post by E Gardner on 2007-10-12
Hi again-

Sorry to keep posting these. I have a MacBook Pro and set up a dual-boot OS X/Ubuntu arrangement by shrinking my Macintosh HD partition with the "diskutil resizeVolume" command. Is there a way to enlarge this partition again, or to restore the entire drive to one continuous HFS+ partition (except for the EFI section at the beginning, of course)?

I am planning on re-arranging my partition setup by creating a shared FAT32 partition for data and moving most non-system/non-application data from my mac partition here, but this means shrinking the HFS+ section further. I want to make sure I'm not doing anything that can't be undone in case the arrangement does not work out. I have of course backed up the entire system to another disk.

Also, are there any known issues with keeping most of my personal files in a FAT32 partition instead of an HFS+ one? I am aware of the 4GB size limit, which doesn't affect me. But will Mac programs that rely on metadata (iPhoto, iTunes, Adobe Bridge, etc.) give me trouble if the files they are working with are not on a journaled filesystem?

---

### Post by pmshirey on 2007-10-13
Try the resize command, maybe it'll let you do it
:popcorn::guitar:

---

### Post by ronocdh on 2007-10-13
I usually use the GParted live CD. I absolutely love it. It even lets you partition visually, by dragging edges of a slider around, similar to how Apple's Boot Camp works, I think. So in some ways it's more pleasant to work with the feature-lacking resizeVolume terminal commands in OS X, IMO.

---

### Post by cyberdork33 on 2007-10-15
you can just use the same command to shrink the partition further. Gparted works as well, and you can even create the FAT32 partition you want too.

---

