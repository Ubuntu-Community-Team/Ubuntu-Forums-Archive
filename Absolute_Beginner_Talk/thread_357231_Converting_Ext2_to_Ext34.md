---
title: "Converting Ext2 to Ext3/4"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by username132 on 2007-02-09
I want to change the format of all my HDs (I have five in total) to Ext2 so Windows and Ubuntu/Suse can all read/write the same drives. If I finally get rid of Windows, can I convert to Ext3 or 4 without reformatting? I don't see why the whole drive should have to be wiped clean just so some journal can be kept somewhere? Am I right?

---

### Post by dannyboy79 on 2007-02-09
it's done with tune2fs. Check out this link: [http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm)

almost every answer you'll ever ask can be found in gogle or by searching this forum first before you post.

---

### Post by igknighted on 2007-02-09
Why not just use ext3 now?  ext4 is not ready yet (although early tests look good), and windows reads ext3 just as well as ext2 (the driver is called ext2, but does both)

---

### Post by username132 on 2007-02-09
Dannyboy, you're right, it has already been asked! That's pretty stupid of me. I normally only search when I figure it's likely to have been discussed before, but since I was expecting to be told I'd have to reformat to get ext2 > ext3, I decided not to check.

Igknighted, if I use Windows to write to a ext3 drive, it breaks the journal, doesn't it? And then it takes hours to fix the journal again using e2fsck? That what I understood from here: [http://www.fs-driver.org/faq.html](http://www.fs-driver.org/faq.html) - it's written for people with a better understanding than mine.

---

### Post by dannyboy79 on 2007-02-09
the fs-driver works fine IF you unmount it safely and correctly. it states it right there in the link you provided: 

If you mount an Ext3 file system as an Ext2 file system and the file system is not cleanly dismounted, (e.g. due to a system crash), you have to run the e2fsck tool. (Linux does it automatically.) Running e2fsck can take several hours on large volumes. You do not benefit from journaling the Ext3 file system, because you have to run e2fsck.  i have used it successfully with a 500gb WD hdd inside a external enclosure that has esata as well as usb. as long as you unmount it correctly in linux and then unmount it correctly from windows you'll be fine. I only use this for movies, pics, etc. not any folders where ownership and permissions is important!

---

### Post by username132 on 2007-02-09
I thought Windows took care of mounting harddrives in the background? When would I need to unmount it manually in Windows or Linux?
I took a long break from Linux, never having really managed to get into it, whilst waiting for SATA issues to disappear and now that they have, I've forgotten what little was once clear.

---

### Post by dannyboy79 on 2007-02-09
because of cache and whether or not the drive's contents are included in indexing (i think). in windows when you want to take a usb flash drive you have to click on the little icon in the lower right and tell it to remove it safely and in linux you have to "unmount" the fs first or you risk damaging the filesystem as well your changes you made sometimes are NOT written to the disk immediately unless you mount your hard drive with the sync option but then you're hard drive would be spinning to much and it would die sooner.

---

### Post by username132 on 2007-02-09
I see. So what unmounting in windows/linux only really applies to external/hot pluggable drives?

---

### Post by dannyboy79 on 2007-02-09
yes

---

