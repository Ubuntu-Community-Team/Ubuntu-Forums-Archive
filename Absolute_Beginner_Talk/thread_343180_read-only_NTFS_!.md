---
title: "read-only NTFS ?!?"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by energiya on 2007-01-21
Hi,
When booting I get this:
```

*Mounting local filesystems...
NTFS-fs warning (device hda1): load_system_files(): Unsupported volume flags 0x4000 ecountered.
NTFS-fs error (device hda1): load_system_files(): Volume gas unsupported system flags set. Mounting read-only. Run chkdsk and mount in Windows.

```
hda1 becomes read-only.

This happens only on my fresh compiled 2.6.19-2 kernel. I activated NTFS support, and NTFS write support.

What could the problem be?

---

### Post by zaratustra on 2007-01-21
NTFS is ussually read-only, and writing into it is possible only if you do not change the size of file or something like that... It's beacuse MS doesn't want to expose right way to write onto NTFS. But, there is always a solution. Search for ntfs-3g kernel module, not in kernel conf, but in aptitude should it be

---

### Post by energiya on 2007-01-21
> **zaratustra said:**
> NTFS is ussually read-only, and writing into it is possible only if you do not change the size of file or something like that... It's beacuse MS doesn't want to expose right way to write onto NTFS. But, there is always a solution. Search for ntfs-3g kernel module, not in kernel conf, but in aptitude should it be

Thanks! I will try that.

---

