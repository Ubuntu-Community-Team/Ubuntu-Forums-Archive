---
title: "Issue with Disk Sizes over Network"
date: 2008-06-17
forum: Apple Hardware Users
---

### Post by TheAlmightySam on 2008-06-17
Hey all.  I'm not quite sure what side of the equation this issue lies on, so I'll give you as much detail as I can.
I have an x86 box running 8.04 that acts as a file server over Samba to my G4 iBook.  I have a link/alias/shortcut/whatever in the Public folder to a HFS 500GB external drive (journaling disabled) that stores most of the media.  However, when I access this link from the iBook, the amount of free space is reported incorrectly.  It only shows the amount of free space on the internal drive, not the amount of space on the external.

Is there an easy fix for this behavior?

Thanks!

---

### Post by cyberdork33 on 2008-06-17
> **TheAlmightySam said:**
> Hey all.  I'm not quite sure what side of the equation this issue lies on, so I'll give you as much detail as I can.
I have an x86 box running 8.04 that acts as a file server over Samba to my G4 iBook.  I have a link/alias/shortcut/whatever in the Public folder to a HFS 500GB external drive (journaling disabled) that stores most of the media.  However, when I access this link from the iBook, the amount of free space is reported incorrectly.  It only shows the amount of free space on the internal drive, not the amount of space on the external.

Is there an easy fix for this behavior?

Thanks!
no. It is correctly reporting the size of the share, which is the internal drive. 

I think that creating a share for the external's mount point (or a folder on the external) will give you the right information, or you can just run 'df -H' in an ssh terminal to check diskspace.

---

