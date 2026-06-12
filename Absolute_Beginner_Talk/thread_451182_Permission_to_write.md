---
title: "Permission to write?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by werle on 2007-05-22
I have an external HD which I use with my xp installation, my xp won\t boot and I need to move some files from my C:drive to the external. Unfortunately I don't have permissions to write on the external. How do I set the permissions so I can write to it_

Thomas

---

### Post by h0ax on 2007-05-22
Because the drive you used with XP is used under XP first it is more than likely an NTFS partition.  By default, Ubuntu only has read only permissions, like you've stated.
There are lots of tutorials on here talking about NTFS-3g and other means to enable writing to an NTFS partition, I would suggest searching the forums.

---

### Post by werle on 2007-05-22
Hmm, does this also apply when I wan't to copy files from one ntfs partittion to another?

Thomas

---

### Post by Outrunner on 2007-05-22
Ubuntu(and Linux in general) cannot write natively to a NTFS partition, so yes it does apply, you'll need to get ntfs-3g to write to a NTFS partition. I recommend looking in the Tutorials forum.

---

