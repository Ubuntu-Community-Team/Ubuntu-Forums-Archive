---
title: "Formatting an external hard drive"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-16
I plan on buying an external a hard drive to share between a linux and windows machine. I suppose my only option for a file system to do this would be FAT? Is there a tool within  Ubuntu that will allow me to do the formatting, or do I have to use something like the Ultimate Boot CD? What are the advantages of FAT over EXT3 besides being able to work with Windows? What are the advantages over EXT3 over FAT?

---

### Post by jken146 on 2007-12-16
FAT is not your only option, because Ubuntu has built-in NTFS read/write support (since Gutsy).  There is also an ext3 driver for Windows.  [www.fs-driver.org](www.fs-driver.org)

Ext3 is better as a filesystem because it supports file permissions and it never needs to be defragmented like the Windows filesystems do.  The only disadvantage of using ext3 that I can think of is that when ou write to it in Windows, your permissions may get a bit messed up (can be fixed of course with sudo chown and sudo chmod commands though, but it's not ideal to be doing this all the time).

---

### Post by viking777 on 2007-12-16
> **jken146 said:**
> There is also an ext3 driver for Windows.

Wow! I never knew that. 

Pity it doesn't work on 64bit though it might have been useful.

---

### Post by fmbugdadi on 2007-12-16
Good information. Thanks a lot.

---

