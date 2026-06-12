---
title: "Problems with Gnome File Browser after Upgrade"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by uriahs on 2006-12-11
A week or so ago, the Update Manager popped up with some updates for Gnome and such (Not sure if nautils was part of this update session). I installed the updates and have been having problems with the File Browser (nautils) since, however I have not restarted.

I have an intermittent problem with launching Gnome for a specific directory. If it happens it launches about 5 Gnome browsers to my home directory and 1 to the actual directory I wanted to go to.

Another problem I just encountered was mounting an encrypted volume using TrueCrypt and moving some files into a new directory with an all uppercase name. It then moved them into a directory with an all lower case name and an all uppercase name. I went to move them from the all uppercase directory to the all lowercase directory and it deleted all of the files. I am unsure if they are lost in the ether or if they are in some obscure trash file or can be recovered.

I also can now, no longer unmount my secure partition as it says:
umount: /mnt/secure: device is busy
umount: /mnt/secure: device is busy
truecrypt: Cannot dismount /dev/mapper/truecrypt0

I have just killed the nautils process and it has restarted it's self, hoping the problems don't come back. However I still can't unmount my drive.

Anyway of figuring out what is locking it?

Or forcievly dismounting it?

Or anyother help at all?

---

### Post by uriahs on 2006-12-11
Well mounting another encrypted partition and then unmounting all partitions using truecrypt -d seem'd to fix the locking problem.

The nautils killing seems to have fixed that problem in the mean time, well so far at least.

---

