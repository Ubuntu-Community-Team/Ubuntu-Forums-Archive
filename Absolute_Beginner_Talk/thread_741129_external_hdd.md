---
title: "external hdd"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by sevr2k on 2008-03-31
hey, i have a question. on one box i am running ubuntu and on my other box windows. i have a external hdd hooked up to the windows box with about 250gigs of media on it. well i am gonna let my roommate use the windows box so i need to take the external to my ubuntu box. since it was formatted and everything to work with windows is there anyway to hook it up to linux and keep everything on it. thanks in advance.

---

### Post by himynameisdaniel on 2008-03-31
Should be no problem doing it, just plug it strait in, mine works fine.

---

### Post by saj0577 on 2008-03-31
Depends what format you formatted it in whether you may need to do a little work to edit the files.

Saj

---

### Post by warp99 on 2008-03-31
Sure, just plug it in. If the drive is formatted FAT32 Ubuntu should see the drive no problem. If the drive is NTFS the you need to have the ntfs-3g drivers loaded and for easy configuration I would suggest the ntfs-config program in the universe repositories.

Edit:

I assume that the external HDD is using the usb port.

---

### Post by sevr2k on 2008-04-03
its actually an esata hookup because the windows system doesnt have usb 2.0, is this going to matter?

---

