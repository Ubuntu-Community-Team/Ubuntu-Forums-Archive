---
title: "Mac OS 9 Install Disc Won't Read Xubuntu Hard Drive"
date: 2007-02-11
forum: Apple PPC Users
---

### Post by LampshadeRevolver on 2007-02-11
I had a PowerPC G3 with Mas OS 10.4 on it, and somewhere down the line I decided to put Xubuntu on it because it was running like a behemoth. I'll be honest: Linux is not for me, for a multitude of reasons. So I dug up an old Mac OS 9 install disc and ran that. The problem is, it won't acknowledge my hard drive, and won't install itself without a destination disk.

Any suggestions?

---

### Post by Ptero-4 on 2007-02-11
Lampshaderevolver. You will need to run the ¨Disk Setup¨ (or something similar, I haven`t used OS9 in a while) utility to format the HD, that`s because OS9 doesn`t have the modules needed to read the Linux filesystem.

---

### Post by grazie on 2007-02-12
Not actually done this, so this is a suggestion in case nobody posts a known solution. Use at your own risk.

Use your OS X install disk to create an OS 9 partition and leave the rest as free space. Just create one partition and tick the checkbox for OS 9 compatability in the disk utility (Installer > Open Disk Utillity) This will create the essential OS 9 partitions, but you'll probably need to wipe the disk first.

Then install OS 9 followed by Xubuntu.

---

### Post by 3rdalbum on 2007-02-12
The utility is called Drive Setup, and it's on the Mac OS 9 disc. Use that to format and repartition the hard drive into one HFS+ volume. Once that's done, use the normal Mac OS 9 installer.

Actually, I recommend two partitions - one for the operating system, the other for programs and documents. That way you'll go longer in between reinstalls of the OS.

---

