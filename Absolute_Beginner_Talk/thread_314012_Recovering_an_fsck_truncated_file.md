---
title: "Recovering an fsck truncated file"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by pnavin on 2006-12-06
Hi everyone!

I've been mucking around with Linux for a while now, but not seriously.  Lately I've installed Ubuntu 6.06 (dual boot with Windows XP) on my Dell XPS1210 laptop.  It's really quite nice, but this morning it did something I didn't expect.  I have a Word document that I use quite frequently for receipts and notes.  I've been using OpenOffice to edit it for quite a while now in Windows and Linux (it's on a FAT32 partition).  This morning, when I booted up, fsck did its thing (it always does a check, I think), but it came up with an error.  Something about the file was wrong, so it truncated its size to zero!  So I was wondering, could someone please tell me how I can get it back?  And possibly why it happened?  Any help would be greatly appreciated!

Cheers,
   -Paul.

---

### Post by bapoumba on 2006-12-07
Hi,
first thing, do you have any backup ?
Then did you happen to note the fsck output ?
You might want to check [dosfsck]("http://www.linuxmanpages.com/man8/dosfsck.8.php").

---

