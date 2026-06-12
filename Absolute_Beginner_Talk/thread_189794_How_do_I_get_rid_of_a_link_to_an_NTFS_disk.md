---
title: "How do I get rid of a link to an NTFS disk?"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by jonboy99 on 2006-06-05
Aargh!  Somehow made a link (while root) to my windows disk, which is NTFS.  The NTFS disk is of course read only.
I don't want the link anymore, but when I try and delete it, even as root, it won't let me.  When I try and change the permissions of the link to write, it says (even when i'm root):

'couldn't change the permissions of "link to hda1" because it is on a read only disk'

So has it put the link on the NTFS volume itself?  How do I get rid of it?

Cheers
Jon

---

### Post by anaconda on 2006-06-05
edit your 
/etc/fstab   -file

remove the line that refers to hda1
Or just commen it away by adding a # in front of the line.

After you boot your windows disk wont be available anymore.

If you want it back you can uncomment the line and boot again...

---

### Post by anaconda on 2006-06-05
Oh..

I know you dont really have to boot, but forgot how to "re-run" fstab file...

---

