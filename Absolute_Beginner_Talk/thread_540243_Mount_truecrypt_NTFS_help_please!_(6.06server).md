---
title: "Mount truecrypt NTFS help please! (6.06server)"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by viktor-sama on 2007-09-01
Hello,
I need some help to mount a windows (NTFS) truecrypt hard-driver.
I do only need to have it in read-only mode, and I'm running 6.06 LTS Server install.
I have it mounted now and I cane see the first directories on the driver but then I try to cd /media/truecryp/harddrive/ it's say that  the command cd is not found (work on any other directory)

---

### Post by Trevster on 2007-09-02
Hi,

Not exactly sure what you are asking so forgive me if you know all this.

You need to specify a mount point for the drive like:

truecrypt  /dev/hda2 /mnt/tc

to mount the drive  at /mnt/tc

to enable ntfs read and write you need the option ntfs-3g

truecrypt --mount --filesystem ntfs-3g /dev/hda2  /mnt/tc/ #the mount point.

Hope that helps.

---

### Post by viktor-sama on 2007-09-02
Thanks, It helped I didn't know I hade to d write  ntfs-3g to get  it work. ;p

---

