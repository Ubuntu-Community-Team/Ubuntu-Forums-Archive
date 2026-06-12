---
title: "What type of format?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Faledask on 2007-10-19
okay I renstalled XP and Ubuntu on my frist drive. On the second drive I made the swap at the beginning and I wanted to make the rest of the drive shareable data between XP and Ubuntu. what type of formating can they both read and write on?

---

### Post by asimon on 2007-10-19
Ubuntu can nowadays read and write Windows' NTFS filesystem just fine. So I recommend to use NTFS.

Just don't install Linux on a Windows filesystem (may it VFAT or NTFS). The reason is that these Windows filesystems don't support Linux' file permission system (and the extended file attributes, but the later is not that important). So always use an extra partition for shared access.

See [MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) for more information.

---

### Post by Frak on 2007-10-19
Go for NTFS, support is 100% stable and writes pefectly.

---

