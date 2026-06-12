---
title: "There are differences between boot sector and its backup"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by jano_rajmond on 2007-07-19
I get the error message "There are differences between boot sector and its backup" every time I start Ubuntu on 3 different partitions.

The first one is not specified... so I guess it's Ubuntu's file system partition, the next two are "dev/hda1" and "/dev/hda7".

I also had this error on "/dev/hda8" but this was fixed by typing (as root):

```
umount /dev/hda8
fsck.vfat /dev/hda8 -ar

```

This promted me if I wanted to "Copy backup to original" or "Copy original to backup". I chose to copy the original to backup (as the original was correct as it booted ok).

I tried doing the same thing for "/dev/hda7" but after I choose "Copy original to backup" I just get "Leaving file system unchanged".

Also how do you proceed for the filesystem?

I know that as long as Ubuntu boots and runs it's not a big problem, but it just bugs me.

I also read something about modifying the "/etc/fstab" but didn't quite understand what values to change from "1" to "0" there so please explain... and also I don't think that would help as it would still scan the root partition and it seems there are differences there too.

Pls help and explain thoroughly... If you can't do that then pls don't answer.

THNX!!!

---

### Post by dptxp on 2007-07-19
If there is an offset between between boot sector and backup, run the following command as root:

fsck.vfat /dev/sda1

For you it may be hda1 NOT sda1.


It takes some time, so wait, then copy original to backup when you are required to choose.

---

### Post by jano_rajmond on 2007-07-20
Oh... come on! Have you read my post at all?!?!?!?

I already did that! I tried to write the original to backup... it just throws out "File system left unchanged" after a few seconds!


ANYTHING ELSE?!?!?!??!?!?!??!?!?!?!??!?! :confused:

---

### Post by dptxp on 2007-07-20
Yes, I missed.
Your file system may not be vfat (fay32), so why not enter correct one instead of vfat ?

---

### Post by Mornedhel on 2007-07-20
Nah, I got the same error, and the fsck man page states somewhere these errors will not be fixed by a fsck in vfat mode. My workaround was to edit the fstab not to check the partition at start-up (man fstab or man /etc/fstab, don't remember and cannot check since I am not on my computer)

---

### Post by jano_rajmond on 2007-07-20
Yes, managed to edit /etc/fstab so it does not scan at startup.

Thnks to all!

---

