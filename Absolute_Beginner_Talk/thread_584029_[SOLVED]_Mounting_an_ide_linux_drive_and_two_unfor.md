---
title: "[SOLVED] Mounting an ide linux drive and two unformated sata drives"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by TehLeProsy on 2007-10-20
I am trying to mount a ide drive that I previously installed ubuntu( i want to get some file off it, then  re-format it), and two sata drives that I formated with the winxp partition tool(the are not ntfs, as I only deleted the partitions, but didn't actually reformat them).

As far as linux and command line I am a total noob, I know to mount the drive I need to make a media directory and edit fs-tab, but I am not sure what to add to fstab and I don't know what to call the fs on the sata drives or the ide drive. 

I have looked at fdisk -l and ubuntu is seeing my drives, the sata are showing up as sda and sdb,
also the ide drive I want to mount is shown as sdb in device manager, but the fstab file only has a hard drive entry for hda.

I think I am probably making this more complicatred then it needs to be.
Any suggestions would be greatly appreciated.
Thanks.

---

### Post by Roofie on 2007-10-20
Try here it is a very good place for what you need 
```
http://www.psychocats.net/ubuntu/mountlinux
```

---

### Post by TehLeProsy on 2007-10-20
ok, I was wrong both my hda and hdb are mounted, but the size reported by the filesystem is wrong, in fdisk it shows up as a 203 gig disk, but the filesystem shows it as being 107gig free with 40 gig being used. would the hd2 and hd5 partions realy take up an extra 40 0r 50 gig by default?

---

### Post by TehLeProsy on 2007-10-20
Oh thanks Roofie, Sry I didn't see your post at first that looks like it may be what I need.
I am still a little confused about size discrepencys on my hdb.
Thanks.

---

