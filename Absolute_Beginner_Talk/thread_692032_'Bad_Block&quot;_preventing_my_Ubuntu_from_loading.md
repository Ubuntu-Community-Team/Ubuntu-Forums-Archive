---
title: "'Bad Block&quot; preventing my Ubuntu from loading."
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by DasMatts on 2008-02-09
Hey All, 

After my Ace Laptop attempted to do a forced check, FF would not load as it said there was a bad block. Furthermore, it said this : inode 211411: 4343008 and Inode 2162975:4343008. I have even tried to load FF in recovery mode and yet it will not load. Any ideas?

---

### Post by codeslicer on 2008-02-09
I would run this:
```
sudo fsck /
```
but a dialog says you might create severe damage. How did you install Ubuntu? If you still have the CD, go in it, find the location of your Ubuntu drive (Not filesystem, that's the filesystem for the live cd), which should be marked as something like 20GB Volume or similar to that. Once you do that, run that command but replace the "/" with the location of the Ubuntu installation on the harddrive :)

---

### Post by DasMatts on 2008-02-09
I no longer have the cd as my friend installed the system. Do you have a way for me to actually get into the OS so I can run the code? AS of right now it will not go past the system check at boot up.

---

### Post by corney91 on 2008-02-09
> **DasMatts said:**
> I no longer have the cd as my friend installed the system. Do you have a way for me to actually get into the OS so I can run the code? AS of right now it will not go past the system check at boot up.
You'll need a LiveCD to boot into the system without using your harddrive. Then run:```
sudo fsck /dev/[name of partition]
```

To find out the name of the partition run```
sudo fdisk -l
```

And whatever you do, don't EVER run fsck on a mounted filesystem!

Hope this helps:)

---

