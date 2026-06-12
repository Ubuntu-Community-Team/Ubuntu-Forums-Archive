---
title: "Triple Boot Partition Table"
date: 2007-08-02
forum: Apple Intel Users
---

### Post by black_raven2525 on 2007-08-02
Currently, my partition map is

1#EFI
2#OSX
free space
3#WinXP

I want to add Ubuntu in that free space because I hear that if windows isn't last, it throws a fit and wont boot.  The question I have is whether or not windows has to be numerically last as in:

1#EFI
2#OSX
3#Ubuntu
4#WinXP

If I run the Ubuntu installer it wants to setup the table as:

1#EFI
2#OSX
4#Ubuntu
3#WinXP

Will this be a problem?  If so, how do I reassign the partition numbers to make Windows happy?

---

### Post by cyberdork33 on 2007-08-02
try using the gparted live cd. I got it to fill in missing numbers somehow.

You wouldn't be able to boot ubuntu that way anyway since you can only boot legacy OSs from the first 4 partitions.

---

### Post by black_raven2525 on 2007-08-02
How is that violating the first 4 partitions? I know I wouldn't be able to have a swap partition, Ive already read the howto on swap files.  Ive already been messing with the Gparted LiveCD but I have yet to find away to change the partition numbers.

---

### Post by cyberdork33 on 2007-08-02
> **black_raven2525 said:**
> How is that violating the first 4 partitions? I know I wouldn't be able to have a swap partition, Ive already read the howto on swap files.  Ive already been messing with the Gparted LiveCD but I have yet to find away to change the partition numbers.

The emulated BIOS cannot see more that the first 4 partitions.  I thought you were saying that WinXP was already labeled as sda4, so nevermind. I am not sure if it will work or not with windows not being last. A lot of users in the Triple booting thread were saying that windows did not need to be last, but that might be for Vista.

---

