---
title: "NTFS Under Linux"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by dmallo on 2006-09-23
I know that it is possible to get read/write NTFS support through the ([Linux NTFS]("wwww.linux-ntfs.org")) project. Can linux tolerate having a home directory on an NTFS partition?

I understand that Linux uses flags in its filesystems that designate whether a file is executable or not (while Windoze uses file extensions). And Linux uses access control to keep other users from accessing a user's files. Will all of these still work under NTFS?

It would be nice if I could get Windows and Linux to both read/write to the same hard drive/partition. Since Microsoft won't let Windows Vista run unsigned drivers :mad:, Linux has to read/write to a Windows-compatible filesystem. Furthermore, it's a big hard drive (320GB), and AFAIK FAT doesn't scale that big.

Thanks in advance!

---

### Post by insane_alien on 2006-09-23
i don't think so. NTFS isn't so hot at permissions. ext3 is better anyway. doesn't need defrag and supports the permissions system.

---

### Post by Sef on 2006-09-23
> It would be nice if I could get Windows and Linux to both read/write to the same hard drive/partition. Since Microsoft won't let Windows Vista run unsigned drivers , Linux has to read/write to a Windows-compatible filesystem. Furthermore, it's a big hard drive (320GB), and AFAIK FAT doesn't scale that big.


How big do you want to make your home partition?

---

### Post by xyz on 2006-09-23
If interested:
[by givré]("http://www.ubuntuforums.org/showthread.php?t=217009")my 

I've got it on Toshiba and it works. I have however not installed the latest updates since I locked my kernel updates for the time being.

---

### Post by dyssident on 2006-09-23
i would recomend creating a symlink from your home folder your home folder on your windows partition. you could probably do what youre suggesting, but youre asking for problems.

if you want read+write access, ive created a package to automagically do the setup in the above mentioned thread. [you can find it here](http://www.ubuntuforums.org/showthread.php?t=255896).

---

### Post by xyz on 2006-09-23
Great job dyssident...thanks and bravo!

---

